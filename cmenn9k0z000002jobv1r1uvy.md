---
title: "How to Use Docker: A Complete Tutorial"
seoTitle: "Docker Tutorial: Complete Guide"
seoDescription: "Explore a comprehensive Docker tutorial to create and manage containers, including setup, commands, port mapping, and Docker Compose"
datePublished: Sat Aug 23 2025 02:32:41 GMT+0000 (Coordinated Universal Time)
cuid: cmenn9k0z000002jobv1r1uvy
slug: how-to-use-docker-a-complete-tutorial
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1755766877666/69cb2bc0-7e33-47ce-b49c-28e5509bcc8f.png
tags: docker, web-development, full-stack, docker-compose, docker-images

---

## What is Docker?

Docker is a tool that helps you create and manage containers. Containers are lightweight and portable packages that include your application and everything it needs to run in different environments.

## Why do we need to use Docker?

Every developer has faced a frustrating situation: you spend hours building a feature, everything works perfectly on your machine, but when your teammate runs the same code, it fails.

Docker fixes these issues by packaging your application with its entire environment, including the exact software versions, libraries, and settings needed to run. When you share a Docker container, you are sharing the complete working environment, not just the code.

## What are Containers?

Containers are simple, portable packages that include everything your application needs to work. They contain:

* Your application code
    
* The runtime environment, like Python or Node.js
    
* The system libraries and dependencies
    
* The configuration files and settings
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755510909818/a925518b-6a8a-43c1-97d2-365c2dde6c35.png align="center")
    

## Docker Installation and Setup

I downloaded and installed Docker Desktop on my Windows computer without any issues. Once installed, I opened Docker Desktop, and the icon appeared in the system, indicating it was running.

To confirm the installation, I ran the command:

```bash
docker -v
```

This showed Docker was correctly installed. I then tested it by running:

```bash
docker run hello-world
```

The test image pulled successfully, confirming everything was working. Now I’m ready to create and manage containers easily.

## What are Docker containers and Images?

A Docker image is a template used to create containers. It includes your application code, all necessary dependencies, and configuration files, allowing the app to run consistently every time.

A Docker container is a running version of a Docker image. You can think of it as an object created from that template. Containers provide isolated environments in which your application can run. This means:

* Any data or changes made inside one container stay within that container.
    
* One container cannot access the data or resources of another container, which keeps everything secure and separate.
    

You can create custom Docker images to meet your specific needs by adding your application code, tools, and settings. Once you create these custom images, you can share them on platforms like Docker Hub or use them in different environments.

Here are some important Docker commands to remember:

* `docker container ls` — Lists all the running containers on your machine.
    
* `docker start <container_name>` — Starts a container that has been stopped.
    
* `docker stop <container_name>` — Stops a running container.
    
* `docker exec -it <container_name> bash` — Opens an interactive terminal inside a running container.
    

You can download images created by others from Docker Hub using the `docker pull` command. These commands help you manage containers and interact with the environments where your applications run.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755510874949/dde658b4-8465-4309-8bac-a0f35f543a48.png align="center")

## Port Mapping in Docker

**What is Port Mapping?**  
Port mapping is a Docker feature that connects ports on your computer to ports inside a Docker container. It allows outside traffic to reach services running inside the container.

**Why Do We Need It?**

* **Container Isolation:** Docker containers are isolated from the host network by default.
    
* **External Access:** Without port mapping, you can't access web apps, APIs, or databases inside containers.
    
* **Development Testing:** You can test applications in containers locally before deploying them.
    
* **Service Communication:** It allows host applications to communicate with services inside containers.
    
* **Multiple Environments:** You can run the same container on different ports for development, staging, and testing.
    

**Basic Syntax:**

```bash
docker run -p HOST_PORT:CONTAINER_PORT image_name
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755682401060/2020be84-3fe0-4f76-8dca-6c27441582e2.png align="center")

### **Step-by-Step Example: Nginx Web Server**

**Step 1: Run the container with port mapping**

```bash
docker run --name my-web -p 8080:80 -d nginx
```

This command does the following:

* It runs the Nginx container in the background (-d).
    
* It maps your computer's port 8080 to the container's port 80.
    
* Nginx listens on port 80 inside the container.
    
* Your computer forwards traffic from port 8080 to the container's port 80.
    

**Step 2: Access the application**

* Open a browser and go to:  
    [http://localhost:8080](http://localhost:8080)
    
* Or test with curl:
    

```bash
curl http://localhost:8080
```

**Step 3: Verify the mapping**

```bash
docker ps
```

You should see: 0.0.0.0:8080-&gt;80/tcp

**Key Takeaway:**  
The port mapping format is always HOST\_PORT:CONTAINER\_PORT. The host port is how you access the application, while the container port is what the application listens to inside the container.

## Environment Variables

Environment variables are key-value pairs that provide settings to Docker containers during runtime. They enable you to adjust your application behaviour without modifying the code or rebuilding the container image.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755751112920/eafaf244-ecdf-4bb4-a661-6be8125a5206.png align="center")

### Why do we need environment variables?

1. Same Image, Different Environments: You can use a single container image for development, staging, and production, with distinct settings for each environment.
    
2. Security: You can store passwords and API keys safely, avoiding hardcoding them in images.
    
3. No Code Changes: You can change how the app behaves without modifying the source code or rebuilding the images.
    
4. Runtime Control: You can enable or disable features, change ports, or adjust settings while the app is running.
    
5. Cost-efficient: You don’t need separate images for each environment.
    

**Basic Usage Example: To use a single variable, run:**

```bash
docker run -e VARIABLE_NAME=value image_name
```

## Containerising Node.js application

**Containerising a Node.js Application**

1. **Create the Dockerfile**
    

A Dockerfile is a text file that tells Docker how to build your application image. Put this file in the main folder of your Node.js project.

2. **Build the Docker Image**
    

Once your Dockerfile is ready, build the image from the command line in your project’s root folder. Use the command below.

```bash
docker build -t my-node-app .
```

Here, `-t` Tag your image with a name you choose (like "my-node-app"). The `.` means use the current folder for building the image.

3. **Run the Container with Port Mapping**
    

After successfully building the image, you can run it as a container. Use the command below.

```bash
docker run -d -p 8080:3000 --name my-running-app my-node-app
```

The `-d` flag runs the container in the background. The `-p` flag maps ports. Here, it connects port 8080 on your computer to port 3000 in the container. You can access your application at [http://localhost:8080](http://localhost:8080).

4. **Publish to Docker Hub**
    

If you want to share your image with others or deploy it, you can publish it on Docker Hub.

**Step 1: Log In**

Log in to your Docker Hub account from the terminal.

```bash
docker login
```

**Step 2: Re-Tag the Image**

Change your image tag to include your Docker Hub username.

```bash
docker tag my-node-app your-dockerhub-username/my-node-app
```

**Step 3: Push the Image**

Finally, upload the tagged image to Docker Hub.

```bash
docker push your-dockerhub-username/my-node-app
```

Your image is now ready for others to pull and use.

%[https://github.com/abdultalha0862/Docker] 

## Docker Compose

Docker Compose is a tool that helps you manage applications with multiple Docker containers. You use a single file `docker-compose.yml` to define and run all parts of your application together. Think of it as a plan for your entire app, including your website, database, and cache.

**Key Features**

* **Simple Setup**: You can define your whole multi-container setup in one easy-to-read YAML file.
    
* **Single Command Control**: Start or stop all your containers with commands like `docker-compose up` and `docker-compose down`.
    
* **Automatic Networking**: The services in your file can communicate easily over a shared network.
    
* **Consistent Environments**: Your app will run the same way on any machine that has Docker installed.
    

**The** `docker-compose.yml` File

This file is the main part of Docker Compose. Here’s a quick look at what it looks like:

```yaml
version: '3.8'
services:
  postgres:
    image: postgres
    ports:
      - "5432:5432"
    environment:
      POSTGRES_USER: postgres
      POSTGRES_DB: review
      POSTGRES_PASSWORD: password
  redis:
    image: redis
    ports:
      - "6379:6379"
```

**Essential Commands**

Run these commands in the directory where your `docker-compose.yml` file is stored.

* `docker-compose up`: Start your entire application. (Add `-d` to run in the background).
    
* `docker-compose down`: Stop and remove all containers, networks, and resources.
    
* `docker-compose ps`: Show all running containers for your application.
    
* `docker-compose logs`: View logs from all services. (Use `docker-compose logs -f <service_name>` to follow logs for one service).
    
* `docker-compose build`: Rebuild the images for your services if you have changed the Dockerfile.
    
* `docker-compose exec <service> <command>`: Run a command inside a running container (e.g., `docker-compose exec web sh`).
    

## Docker Networking

Docker networking is essential for enabling communication between containers and external systems. It offers several options:

1. **Bridge Network**: The default mode, allowing containers on the same host to communicate through assigned IP addresses or container names.
    
    ```bash
    docker run -d --name web nginx
    docker run -d --name db postgres
    ```
    
2. **Host Network**: The container shares the host’s network stack, using the host's IP address instead of its own. This improves performance but decreases isolation.
    
    ```bash
    docker run -d --network host nginx
    ```
    
3. **None Network**: No networking provided, ideal for isolated containers that don’t need external communication.
    
    ```bash
    docker run -it --network none alpine
    ```
    
4. **Custom Networks**: Users can create tailored networks (like bridge, overlay, or macvlan) with specific settings for improved flexibility and security.
    

# Challenges and Solutions

1. **Challenge**: Windows didn’t recognise the Docker command ("docker is not recognised").  
    **Solution**:
    

* Ensured the folder `docker.exe` was on my Path (System → Advanced → Environment Variables → Path).
    
* Restarted the terminal.
    
* Verified Docker was available.  
    Resource: [https://stackoverflow.com/questions/49478343/windows-doesnt-recognize-docker-command](https://stackoverflow.com/questions/49478343/windows-doesnt-recognize-docker-command)  
    Result: the Docker command worked in the terminal.
    

2. **Challenge**: `docker compose up` failed with `services.postgres must be array`.  
    **Solution**:
    

* Found a YAML indentation/format error (the `ports` field was not written as a list).
    
* Fixed `docker-compose.yml` So multi-value fields use `-` and correct indentation.  
    Result: `docker compose up` Ran without the error.
    

# Resources Used

1. I explored Docker through Kunal's informative tutorial on YouTube, which provided a clear introduction to the platform's capabilities. You can find it here: [https://www.youtube.com/watch?v=17Bl31rlnRM&t=4017s](https://www.youtube.com/watch?v=17Bl31rlnRM&t=4017s).
    
2. Additionally, I watched Piyush's detailed video tutorial that covered various Docker concepts and practical applications. Check it out at: [https://www.youtube.com/watch?v=31k6AtW-b3Y&t=2511s](https://www.youtube.com/watch?v=31k6AtW-b3Y&t=2511s).