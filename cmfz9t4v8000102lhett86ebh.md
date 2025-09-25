---
title: "Debugging Ghost's ActivityPub Integration: From "Loading Interrupted" to Social Web Success"
seoTitle: "Fixing Ghost for Social Web Success"
seoDescription: "Resolve Ghost's "Loading interrupted" error through correct ActivityPub setup for seamless social web integration"
datePublished: Thu Sep 25 2025 10:28:57 GMT+0000 (Coordinated Universal Time)
cuid: cmfz9t4v8000102lhett86ebh
slug: debugging-ghosts-activitypub-integration-from-loading-interrupted-to-social-web-success
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1758796224210/51090337-cbdd-4204-be7c-0d4a8fab18af.png
tags: ghost, debugging, decentralization, activitypub, federated-social-web

---

## TL;DR

If you see **“Loading interrupted”** under Ghost’s **Analytics → Network** tab, it’s not a traditional analytics issue. It’s because **ActivityPub isn’t configured correctly** in your local setup.

### **The fix:**

* Run supporting Docker services (Caddy, MySQL, Redis)
    
* Set `social_web_enabled: true` in `config.local.json`
    
* Use a clean base URL ([`http://localhost`](http://localhost) not [`http://localhost:2368`](http://localhost:2368))
    
* Proxy `/.ghost/activitypub/*` routes through Caddy
    

This turns the “Network” tab into an **ActivityPub Reader** instead of failing.

## The Story

My journey began with exploring different installation methods, from npm local install to Docker containers, and finally settling on source code installation for maximum control and visibility. I spent time methodically understanding Ghost's monorepo structure, exploring each folder from apps (modular applications) to ghost (core functionality) to grasp how the architecture supports features like ActivityPub.

After successfully installing Ghost from source and configuring the development environment, everything seemed to be working perfectly. The traditional analytics were loading fine, showing member counts and post statistics. But when I clicked on the "Analytics" tab and tried to access the "Network" section, I was greeted with a frustrating **" Loading interrupted"** error.

What I initially thought was a simple analytics issue turned out to be a complex ActivityPub service configuration problem that led me down a rabbit hole of debugging Ghost's social web architecture.

## The Pain Point

### The Mysterious "Loading Interrupted" Error

The problem is displayed in several ways:

1. **Analytics Tab Issues**: The Network section under Analytics would show "Loading interrupted" instead of the expected ActivityPub reader interface
    
2. **404 Errors Everywhere**: Ghost logs were filled with ActivityPub endpoint failures:
    
    ```bash
    INFO "GET /.ghost/activitypub/v1/feed/reader/" 404 52ms
    INFO "GET /.ghost/activitypub/users/index/" 404 56ms
    INFO "GET /.ghost/activitypub/v1/account/me/" 404 25ms
    ```
    
3. **Webhook Secret Errors**: The ActivityPub service couldn't initialise:
    
    ```bash
    ERROR: Could not get webhook secret for ActivityPub
    ERROR No webhook secret found - cannot initialise
    ```
    

### The Root Cause Discovery

After extensive debugging, I discovered that Ghost's "Analytics → Network" tab isn't actually traditional web analytics. Instead, it's an **ActivityPub Reader** that allows you to:

* View your federated social network feeds
    
* Manage ActivityPub followers and following
    
* Monitor social web engagement
    
* Handle ActivityPub notifications
    

The "Loading interrupted" error was occurring because the ActivityPub service wasn't properly configured for local development.

## Solution Framework

### Phase 1: Understanding Ghost's Architecture

Ghost's ActivityPub integration follows a specific development setup:

1. **Multi-Service Architecture**: Ghost core + Caddy proxy + ActivityPub service
    
2. **Routing Requirements**: All `/.ghost/activitypub/*` Requests must be proxied through nginx/Caddy
    
3. **External URL Dependency**: ActivityPub requires external URL exposure for federation protocols
    

### Phase 2: Systematic Configuration

Here's the step-by-step solution framework I developed:

#### Step 1: Install Required Dependencies

```bash
# Install Docker for containerised services
curl -fsSL https://get.docker.com -o get-docker.sh && sudo sh get-docker.sh

# Add user to Docker group
sudo usermod -aG docker $USER

# Install external URL exposure tool (ngrok or Tailscale)
sudo apt install ngrok  # or Tailscale for production
```

#### Step 2: Start Supporting Services

```bash
# Start Ghost's supporting Docker services
cd /path/to/ghost
SSH_AUTH_SOCK=/dev/null docker compose up -d caddy mysql redis
```

#### Step 3: Configure Ghost for ActivityPub

Create config.local.json:

```json
{
    "url": "http://localhost",
    "social_web_enabled": true,
    "enableDeveloperExperiments": true,
    "tinybird": {
        "stats": {
            "endpoint": "http://localhost:7181",
            "token": "local_stats_token"
        }
    }
}
```

#### Step 4: Restart Ghost with New Configuration

```bash
# Stop existing Ghost process
pkill -f "yarn dev:ghost"

# Start with a new configuration
yarn dev:ghost
```

### Phase 3: Verification

Key indicators that the solution worked:

1. **URL Configuration Change**:
    
    * Before: `INFO Url configured as:` [`http://localhost:2368/`](http://localhost:2368/)
        
    * After: `INFO Url configured as:` [`http://localhost/`](http://localhost/)
        
2. **ActivityPub Endpoint Improvements**:
    
    * Before: `404` errors on all ActivityPub endpoints
        
    * After: `301` redirects (proper proxy routing)
        
3. **Network Tab Access**: The Analytics → Network tab loads the ActivityPub reader interface instead of showing "Loading interrupted"
    

### Phase 4: Understanding the Technical Details

The solution addressed several technical requirements:

1. **Base URL Configuration**: ActivityPub federation requires a clean base URL without port numbers
    
2. **Proxy Routing**: Caddy handles routing `/.ghost/activitypub/*` requests to the ActivityPub service
    
3. **Service Dependencies**: The ActivityPub service needs MySQL and Redis for state management
    
4. **External Accessibility**: For full federation, the service needs external URL exposure
    

## Key Takeaways

### For Developers

1. **Read the Official Documentation**: Ghost's ActivityPub service has specific local development requirements that differ from standard Ghost setup
    
2. **Understand the Architecture**: "Analytics → Network" is not web analytics - it's a federated social reader
    
3. **Docker is Essential**: The supporting services (Caddy, MySQL, Redis) are crucial for ActivityPub functionality
    
4. **Configuration Hierarchy**: `config.local.json` overrides `config.development.json` for local customisation
    

### For Ghost Users

1. **ActivityPub is Cutting-Edge**: This feature enables true federated publishing to the social web
    
2. **Development Setup is Complex**: Production deployment will likely be simpler, but local development requires careful configuration
    
3. **Network Tab Power**: Once working, the Network tab provides powerful social web management capabilities
    

### For the Community

1. **Documentation Gaps**: The connection between "Loading interrupted" and ActivityPub configuration wasn't immediately obvious
    
2. **Error Messages Could Be Clearer**: More specific error messages about missing ActivityPub configuration would help
    
3. **Setup Automation Opportunity**: This complex setup process could be automated with scripts
    

## Final Thoughts

What started as a frustrating "Loading interrupted" error turned into a deep dive into Ghost's federated social web architecture. The solution required understanding not just Ghost, but the broader ActivityPub ecosystem and how federated social networks operate.

For anyone implementing Ghost's Social Web features, remember:

* Start with the official ActivityPub development setup instructions
    
* Ensure Docker services are running (Caddy, MySQL, Redis)
    
* Configure the base URL correctly in `config.local.json`
    
* Be patient - this is cutting-edge technology that's still evolving
    

Have you encountered similar issues with Ghost's ActivityPub integration? Share your experiences and solutions in the comments below.