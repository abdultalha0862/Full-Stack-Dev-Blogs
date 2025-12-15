---
title: "From Ghost to Zulip: Setting Up My Local Development Environment"
seoTitle: "Setting Up a Local Dev Environment"
seoDescription: "Guide to setting up a local Zulip development environment with solutions to common issues and insights into modern backend ecosystems"
datePublished: Mon Dec 15 2025 10:14:22 GMT+0000 (Coordinated Universal Time)
cuid: cmj6zye6x000002jsgfdsef6s
slug: from-ghost-to-zulip-setting-up-my-local-development-environment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1765105622943/d98545a8-9068-4e84-9318-a234e8e3bbfc.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1765105648465/7020af91-847c-44c5-be6b-250faddf53b5.png
tags: python, django, opensource, developer, wsl, open-source, zulip

---

## Introduction

Setting up **Zulip locally** is not a typical Django setup.

After contributing to **Ghost**, I wanted to challenge myself with a **larger backend system,** one that reflects real-world complexity. Zulip stood out because of its scale, architecture, and active open-source community.

Zulip is built using:

* Django
    
* Tornado
    
* PostgreSQL
    
* RabbitMQ
    

While the setup process is well-documented, I still faced some issues, especially around Python virtual environments and WSL configuration.

In this post, I’ll walk through:

* How I set up Zulip locally on WSL2
    
* The issues I faced during setup
    
* How I fixed them, including the tricky `activate_this.py` problem
    

If you’re setting up Zulip for the first time, this guide should save you time and effort.

## Who This Post Is For

This post is helpful if you are:

* Contributing to **Zulip** for the first time
    
* Moving from smaller projects to **large backend systems**
    
* Using **WSL2 on Windows**
    
* Facing Python 3.12 or `activate_this.py` issues during setup
    

## Prerequisites for Zulip Local Setup

Before starting, make sure your system meets these requirements.

### General Requirements

* 2GB or more RAM
    
* Stable internet connection
    
* GitHub account
    

### Windows Requirements

* Windows 10 or 11 (64-bit)
    
* Virtualisation enabled (VT-x / AMD-V)
    
* Administrator access
    

## Git and GitHub Setup

If Git is already configured, you can skip this step.

Generate an SSH key:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Copy the public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

Add it to:  
**GitHub → Settings → SSH and GPG Keys**

This allows you to clone Zulip securely.

## Setting Up WSL2 for Zulip Development

> If you’re already using native Ubuntu or WSL2, you can skip this section.

### Enable Virtualization

Enable **VT-x / AMD-V** in your BIOS.

### Install WSL2

```bash
wsl --install
```

This installs Ubuntu automatically.

### Use a Fresh WSL Instance

A clean WSL setup helps avoid conflicts with existing Python or Node installations.

### Enable systemd (Important)

Zulip relies on system services like PostgreSQL, Redis, and RabbitMQ.

Edit the config file:

```bash
sudo nano /etc/wsl.conf
```

Add:

```ini
[boot]
systemd=true
```

Restart WSL:

```bash
wsl --shutdown
```

## Install Required Services

Update your system:

```bash
sudo apt update && sudo apt upgrade
```

Install required services:

```bash
sudo apt install rabbitmq-server memcached redis-server postgresql
```

### Configure RabbitMQ

Edit the config file:

```bash
sudo nano /etc/rabbitmq/rabbitmq-env.conf
```

Add:

```ini
NODE_IP_ADDRESS=127.0.0.1
NODE_PORT=5672
```

## Important WSL Tips

### Use WSL’s Native Disk

Avoid working inside `/mnt/c/...`.

Always work from:

```bash
cd ~
```

### Generate SSH Key Inside WSL

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
cat ~/.ssh/id_ed25519.pub
```

Add this key to GitHub as well.

## Cloning the Zulip Repository

### Fork Zulip

Go to:  
[https://github.com/zulip/zulip](https://github.com/zulip/zulip)  
Click **Fork**.

### Clone Your Fork

```bash
git clone --config pull.rebase git@github.com:YOURUSERNAME/zulip.git
cd zulip
git remote add -f upstream https://github.com/zulip/zulip.git
```

## Running Zulip Locally

### Install Dependencies

This step installs all required dependencies and may take 5–10 minutes.

```bash
./tools/provision
```

### Activate the Virtual Environment

```bash
source .venv/bin/activate
```

### Start the Development Server

```bash
./tools/run-dev
```

Visit:  
[http://localhost:9991](http://localhost:9991/)

## Common Zulip Setup Issues (and Fixes)

### Issue 1: Missing `activate_this.py`

**Error**

```text
FileNotFoundError: No such file or directory ... activate_this.py
```

**Why This Happens**

Zulip now uses **uv**, a modern Python package manager.  
Unlike `virtualenv`, it does not automatically create `activate_this.py`.

Some scripts still expect this file.

**Fix**

Manually create it:

```bash
cat > .venv/bin/activate_this.py << 'EOF'
import os
import site
import sys

bin_dir = os.path.dirname(os.path.abspath(__file__))
os.environ["PATH"] = os.pathsep.join([bin_dir] + os.environ.get("PATH", "").split(os.pathsep))

base = os.path.dirname(bin_dir)
os.environ["VIRTUAL_ENV"] = base

site_packages = os.path.join(base, 'lib', 'python{}.{}'.format(*sys.version_info[:2]), 'site-packages')

prev = set(sys.path)
site.addsitedir(site_packages)
sys.real_prefix = sys.prefix
sys.prefix = base

new = list(sys.path)
sys.path[:] = [i for i in new if i not in prev] + [i for i in new if i in prev]
EOF
```

### Issue 2: Django Not Found (Python 3.12)

**Error**

```text
ModuleNotFoundError: No module named 'django'
```

**Root Cause**

Older scripts used:

```python
sys.version[:3]
```

With Python 3.12, this incorrectly returns `"3.1"`.

**Fix**

Use:

```python
'{}.{}'.format(*sys.version_info[:2])
```

Then re-run:

```bash
./tools/provision
```

## Key Learnings from Setting Up Zulip

### Technical Learnings

* Modern tools like **UV** change long-standing Python assumptions
    
* Understanding virtual environment internals is useful for debugging
    
* A proper WSL2 + systemd setup is critical for backend services
    

### Soft Learnings

* Large codebases require patience
    
* Error messages often point to the real issue
    
* Zulip’s documentation and community are extremely helpful
    

## Conclusion

Moving from Ghost to Zulip has been a rewarding step in my open-source journey.

Zulip’s development environment is complex but well-architected, making it a great project for anyone who wants to grow in **backend engineering**.

If you’re stuck on setup, especially around `activate_this.py` you’re not alone. Once the environment is running, contributing becomes much smoother.

## Resources

* Zulip GitHub: [https://github.com/zulip/zulip](https://github.com/zulip/zulip)
    
* Dev Setup Docs: [https://zulip.readthedocs.io/en/latest/development/overview.html](https://zulip.readthedocs.io/en/latest/development/overview.html)
    
* Zulip Community: [https://chat.zulip.org](https://chat.zulip.org/)
    
* WSL2 Docs: [https://docs.microsoft.com/en-us/windows/wsl](https://docs.microsoft.com/en-us/windows/wsl)
    
* UV Package Manager: [https://github.com/astral-sh/uv](https://github.com/astral-sh/uv)