---
title: "Installing Ghost from Source: A Developer's Journey Through Challenges and Solutions"
seoTitle: "Ghost Installation Guide for Developers"
seoDescription: "Guide on installing Ghost from source: overcome challenges, gain control, access deep learning, and leverage cutting-edge features"
datePublished: Fri Sep 12 2025 09:54:50 GMT+0000 (Coordinated Universal Time)
cuid: cmfgnv6o4000a02jogvhm0gqb
slug: installing-ghost-from-source-a-developers-journey-through-challenges-and-solutions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1757670717933/320916ca-c38f-4881-b92e-172aa5fe0cbf.png
tags: docker, ghost, git, wsl, ghost-platform

---

## Introduction

[Ghost](https://ghost.org/) is a powerful open-source publishing platform designed for modern publishing. While most users install Ghost through `npm` or `Docker` method, installing from source provides developers with complete control over the codebase and the ability to contribute to the project. This blog documents my journey installing Ghost from source, the challenges I faced, and the solutions I implemented.

## Why Install Ghost from Source?

Installing Ghost from source gives more advantages:

* **Full Development Environment**: Access to the complete monorepo structure
    
* **Contribution Capability**: Ability to modify and contribute back to the project
    
* **Learning Opportunity**: Deep understanding of Ghost's architecture
    
* **Customization Freedom**: Complete control over all components
    
* **Latest Features**: Access to cutting-edge development features
    

## Prerequisites and Setup

### System Requirements

* **Operating System**: Ubuntu/Linux (WSL2 in my case) (This is the recommended One You can use WSL in Windows)
    
* **Node.js**: Version 22.19.0 (though v18+ LTS recommended)
    
* **Package Manager**: Yarn v1.22.22
    
* **Git**: For repository management
    
* **Docker**: Optional, for MySQL setup
    

### Initial Environment Setup

```bash
# Check Node.js version
node --version

# Check Yarn version
yarn --version

# Verify Git installation
git --version
```

## Step-by-Step Installation Process

### Step 1: Repository Setup

```bash
# Clone the Ghost repository with submodules
git clone --recurse-submodules https://github.com/TryGhost/Ghost.git
cd Ghost

# Check repository structure
ls -la
# Key directories: apps/, ghost/, e2e/, patches/
```

### Step 2: Initial Installation

```bash
# Run the setup command (only once)
yarn setup
```

This command will:

* Install all dependencies (yarn)
    
* Initialize Git submodules
    
* Set up the database (tries MySQL via Docker, falls back to SQLite)
    
* Configure Git hooks
    

### Step 3: Building Components

```bash
# Build all components including the admin client
yarn build
```

This step builds:

* Admin-X design system and framework
    
* Ghost Admin interface (Ember.js)
    
* Frontend assets and dependencies
    

### Step 4: Starting Development Environment

```bash
# Navigate into the Ghost core folder
cd ghost

# Start Ghost core only
yarn dev:ghost

# Or start everything (Ghost + Admin + Frontend)
yarn dev
```

**Important**: When running yarn dev, make sure you are inside the ghost/ folder (not the root of the repository).

Now visit:

* Blog → [http://localhost:2368/](http://localhost:2368/)
    
* Admin → [http://localhost:2368/ghost/](http://localhost:2368/ghost/)
    

## Challenges Encountered and Solutions

### Challenge 1: Docker MySQL Configuration Failure

**Problem Encountered:**

```bash
invalid spec: :/ssh-agent: empty section between colons
error Command failed with exit code 1
Failed to run MySQL Docker container
```

**Root Cause Analysis:**

* The `SSH_AUTH_SOCK` environment variable was undefined
    
* Docker Compose configuration expected SSH agent forwarding
    
* The compose.yml file contained: `${SSH_AUTH_SOCK}:/ssh-agent`
    

**Solution Implemented:**  
Ghost gracefully handled this by falling back to SQLite:

```bash
# SQLite database initialization proceeded successfully
[INFO] Creating table: newsletters
[INFO] Creating table: posts
[INFO] Creating table: users
# ... (60+ tables created successfully)
[INFO] Finished database init!
```

**Alternative Solution (if MySQL required):**

```bash
export SSH_AUTH_SOCK="/tmp/ssh-agent-dummy"
yarn docker:reset
```

**Key Learning:** Ghost's robust fallback mechanisms ensure development can continue even when preferred configurations fail.

### Challenge 2: Admin Interface Build Crash

**Problem Encountered:**

```bash
[adminX] Killed
[adminX] error Command failed with exit code 137
Error: ENOENT: no such file or directory, open 
'/home/sam/Ghost_Install_From_Source/Ghost/ghost/core/core/built/admin/index.html'
```

**Root Cause Analysis:**

* Exit code 137 indicates the process was killed due to memory constraints
    
* The admin build process crashed during concurrent operations
    
* Required admin files were never generated
    
* Ghost server couldn't serve the admin interface
    

**Diagnostic Process:**

```bash
# Checked for admin files
ls -la /home/sam/Ghost_Install_From_Source/Ghost/ghost/core/core/built/admin/
# Directory didn't exist

# Identified missing dependencies
# admin-x-settings/dist/admin-x-settings.js was not built
```

**Solution Implemented:**

1. **Separate Build Process:**
    

```bash
# Build all components in correct dependency order
yarn build
```

2. **Verification:**
    

```bash
# Confirmed admin files were created
ls -la /home/sam/Ghost_Install_From_Source/Ghost/ghost/core/core/built/admin/
# Now showed: index.html, assets/ directory
```

3. **Successful Admin Access:**
    

* Admin interface became accessible at `http://localhost:2368/ghost/`
    

**Key Learning:** Complex monorepo builds may require separate build steps when concurrent processes exceed system resources.

### Challenge 3: Port Conflict on Restart

**Problem Encountered:**

```bash
(EADDRINUSE) Cannot start Ghost.
"Port 2368 is already in use by another program."
"Is another Ghost instance already running?"
```

**Root Cause Analysis:**

* Previous Ghost instance remained running after interruption
    
* Process didn't terminate cleanly
    
* Port 2368 remained occupied
    

**Diagnostic Process:**

```bash
# Identified conflicting process
lsof -i :2368
# COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
# node    15675  sam   27u  IPv4 103179      0t0  TCP localhost:2368 (LISTEN)
```

**Solution Implemented:**

```bash
# Kill the specific process
kill 15675

# Verify port is free
lsof -i :2368
# No output = port available

# Restart Ghost successfully
cd /home/sam/Ghost_Install_From_Source/Ghost/ghost/core
yarn dev
```

**Key Learning:** Always verify port availability and clean up processes before restarting development servers.

### Challenge 4: Build Dependency Chain Issues

**Problem Encountered:**

```bash
ENOENT: no such file or directory, open 
'../../apps/admin-x-settings/dist/admin-x-settings.js'
ember build --environment=production --silent
error Command failed with exit code 1
```

**Root Cause Analysis:**

* Ghost admin (Ember.js) depends on admin-x-settings
    
* Admin-x-settings wasn't built before admin build attempt
    
* Dependency resolution failed in concurrent build process
    

**Solution Implemented:**

```bash
# Build entire project ensuring dependency order
yarn build
```

Build order executed:

1. `@tryghost/shade:build`
    
2. `@tryghost/admin-x-design-system:build`
    
3. `@tryghost/admin-x-framework:build`
    
4. `@tryghost/admin-x-settings:build`
    
5. `ghost-admin:build`
    

**Key Learning:** Monorepo dependency chains require careful build orchestration, especially in memory-constrained environments.

## Resources Used

### Official Documentation and References

* **Ghost Developer Documentation**: [https://ghost.org/docs/install/source/](https://ghost.org/docs/install/source/)
    
* **Ghost GitHub Repository**: [https://github.com/TryGhost/Ghost](https://github.com/TryGhost/Ghost)
    
* **Ghost Contributing Guidelines**: [https://github.com/TryGhost/Ghost/blob/main/.github/CONTRIBUTING.md](https://github.com/TryGhost/Ghost/blob/main/.github/CONTRIBUTING.md)
    
* **Ghost Developer Community**: [https://forum.ghost.org/c/dev/](https://forum.ghost.org/c/dev/)
    
* **Node.js Documentation**: [https://nodejs.org/docs/](https://nodejs.org/docs/)
    
* **Yarn Documentation**: [https://classic.yarnpkg.com/docs/](https://classic.yarnpkg.com/docs/)
    
* **Docker Documentation**: [https://docs.docker.com/](https://docs.docker.com/)
    

### Development Environment Tools

* **VS Code**: Primary development environment
    
    * **Extensions Used**: Git, Terminal, JavaScript/TypeScript support
        
* **Windows Subsystem for Linux (WSL2)**: Ubuntu environment
    
* **Terminal/Bash**: Command-line operations and script execution
    
* **Git**: Version control and repository management
    
* **Yarn v1.22.22**: Package management and script execution
    
* **Node.js v22.19.0**: JavaScript runtime environment
    

## Key Lessons Learned

### 1\. **System Resource Management**

* **Memory Constraints**: Modern JavaScript builds are memory-intensive
    
* **Process Isolation**: Separate builds when concurrent operations fail
    
* **Resource Monitoring**: Watch for exit code 137 (memory kills)
    

### 2\. **Dependency Chain Understanding**

* **Build Order Matters**: Dependencies must be built before dependents
    
* **Monorepo Complexity**: Modern projects have intricate dependency webs
    
* **Fallback Strategies**: Always have alternative approaches ready.
    

### 3\. **Problem-Solving Methodology**

1. **Read Error Messages Carefully**: Exit codes and stack traces provide crucial information
    
2. **Isolate Components**: Test individual parts when complex systems fail
    
3. **Verify Assumptions**: Check that expected files/processes exist
    
4. **Document Solutions**: Record working commands and configurations
    
5. **Understand Root Causes**: Don't just fix symptoms
    

## Final Thoughts

Installing Ghost from source proved to be both challenging and educational. While the process involved multiple technical hurdles, each challenge provided valuable insights into:

* Modern JavaScript development complexity
    
* Monorepo architecture and dependency management
    
* System resource constraints and optimization
    
* Development environment setup and maintenance
    
* Problem-solving methodologies for complex systems