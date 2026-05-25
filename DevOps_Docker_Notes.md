# DevOps & Docker: Containerization, CI/CD, and Modern Deployment Practices

> *A Class Report on Containerization, CI/CD, and Modern Deployment*
> **Published:** May 7, 2026 | **Tags:** `DevOps` `Docker` `CI/CD` `SDLC` `Linux` `Jenkins` `Python` `Cloud Computing`

---

![DevOps Infinity Loop - Plan, Code, Build, Test, Release, Deploy, Operate, Monitor](images/devops-infinity-loop.png)
*Figure 1: The DevOps lifecycle - a continuous loop connecting development and operations.*

---

## Table of Contents

1. [Introduction: Why Containers Matter](#1-introduction-why-containers-matter)
2. [Timeline of Topics](#2-timeline-of-topics)
3. [Docker: Core Concepts](#3-docker-core-concepts)
4. [Traditional Deployment vs. Containers](#4-traditional-deployment-vs-containers)
5. [SDLC Models & CI/CD](#5-sdlc-models--cicd)
6. [Linux Command Practice](#6-linux-command-practice)
7. [Containers vs. Virtual Machines](#7-containers-vs-virtual-machines)
8. [Cloud Computing Service Models](#8-cloud-computing-service-models)
9. [Jenkins & Data Persistence](#9-jenkins--data-persistence)
10. [Python & PIP](#10-python--pip)
11. [Building a Flask Docker Image](#11-building-a-flask-docker-image)
12. [Image Optimization](#12-image-optimization)
13. [The Universal 5-Step Dockerfile Skeleton](#13-the-universal-5-step-dockerfile-skeleton)
14. [Key Takeaways](#14-key-takeaways)
15. [Quick Reference: Essential Docker Commands](#15-quick-reference-essential-docker-commands)

---

## 1. Introduction: Why Containers Matter

Every developer has heard the dreaded words: *"But it works on my machine."* For decades, this single phrase has been the source of countless late nights, failed deployments, and tense conversations between development and operations teams.

Software that runs perfectly on a laptop suddenly breaks the moment it touches a server - often because of a missing library, a different OS version, or a mismatched configuration.

**Containers solve this problem** by bundling the application together with everything it needs to run - so behavior is identical everywhere, from a developer's laptop to a cloud server.

> 💡 **Core idea:** Ship the environment, not just the code.

---

## 2. Timeline of Topics

| Date | Topic |
|------|-------|
| March 5 | Introduction to Docker and DevOps |
| March 9 | Traditional Software Deployment |
| March 16 | SDLC, Agile, and CI/CD |
| March 19 | Linux Command Practice |
| March 23 | Why Docker, Containers vs Images, Cloud Computing |
| March 26 | First Hands-on with Containers |
| March 30 | Docker Exec and Jenkins Installation |
| April 16 | Jenkins, MAC Addresses, Data Persistence |
| April 20 | Python, PIP, and Programming Tasks |
| April 23 | Building the First Flask Docker Image |
| April 26 | KodeKloud Lab: webapp-color and Image Optimization |
| April 27 | The Universal 5-Step Dockerfile Skeleton |

---

## 3. Docker: Core Concepts

### What is Docker?

> *Docker is a platform that allows developers to create, package, and run applications inside containers.*

A **container** includes the application along with everything it needs to run - libraries, dependencies, and configuration files. This bundling makes the application behave the same way on any computer or server.

![Dockerfile to Container workflow - Create Dockerfile, Add instructions, Build image, Run container](images/dockerfile-workflow.png)
*Figure 2: The four-step process from a Dockerfile to a running container.*

---

### Why Docker?

| # | Reason | Explanation |
|---|--------|-------------|
| 1 | **Consistency** | Runs the same on any computer, server, or cloud |
| 2 | **Easy Deployment** | Applications can be packaged and deployed quickly |
| 3 | **Dependency Management** | All required libraries travel together with the app |
| 4 | **Isolation** | Each app runs in its own container - no interference |
| 5 | **Efficient Resource Usage** | Uses fewer resources than virtual machines |
| 6 | **Simplified Dev & Testing** | Test in the exact same environment used in production |
| 7 | **CI/CD Support** | Integrates naturally into automated pipelines |
| 8 | **Scalability** | Spin up multiple identical containers in seconds |

---

### Docker Architecture

![Docker Architecture - Client, Host, Daemon, Images, Containers, Registry](images/docker-architecture.png)
*Figure 3: Docker's six architectural components and how they interact.*

| Component | Role |
|-----------|------|
| **Docker Client** | Interface for running commands (`docker build`, `docker run`, `docker pull`) |
| **Docker Host** | The system where Docker runs; contains the engine, containers, and images |
| **Docker Engine (Daemon)** | Core component that builds, runs, and manages containers |
| **Docker Images** | Read-only templates used to create containers |
| **Docker Containers** | Running instances of Docker images |
| **Docker Registry** | Storage location for images (e.g., Docker Hub) |

---

### CI/CD Overview

| Term | Meaning |
|------|---------|
| **CI - Continuous Integration** | Automatically integrates and tests code changes whenever a developer pushes |
| **CD - Continuous Delivery** | Automatically prepares a release-ready build after CI passes |
| **CD - Continuous Deployment** | Automatically deploys to production without manual intervention |

---

### Docker Editions

| Feature | Community Edition (CE) | Enterprise Edition (EE) |
|---------|----------------------|------------------------|
| Cost | Free | Subscription required |
| Users | Developers, students, small projects | Large companies |
| Support | Community forums | Official Docker support |
| Security | Basic | Advanced and compliant |
| Updates | Frequent | Stable, tested releases |
| Use Case | Learning and development | Production at scale |

---

## 4. Traditional Deployment vs. Containers

### The Old Manual Way

```
Physical server → Install OS → Install dependencies → Copy code → Configure → Start app
```

For a web application this meant: buying a physical server, installing Linux, setting up the database and programming tools, uploading the code, and finally running it. Every single step was done by hand.

![Traditional Deployment vs Docker Containers side-by-side diagram](images/traditional-vs-docker.png)
*Figure 4: Traditional bare-metal deployment (left) vs. Docker containerized deployment (right).*

### Problems with Traditional Deployment

| Problem | Impact |
|---------|--------|
| Time-consuming setup | Reading docs, installing packages, and maintaining them manually |
| Hard to replicate | Migrating to a new server is nearly as much work as starting from scratch |
| Error-prone | Many manual steps = many chances for human error |
| Environment drift | "Works on my machine" - dev and prod environments differ silently |
| Dependency conflicts | App A needs library v1.2, App B needs library v2.0 on the same server |
| Poor scalability | Scaling means buying and configuring more physical machines |

---

## 5. SDLC Models & CI/CD

### What is SDLC?

> *SDLC (Software Development Life Cycle) is a structured framework that defines the overall process of software development from inception to retirement.*

![SDLC Phases - Planning, Analysis, Design, Development, Testing, Deployment, Maintenance](images/sdlc-phases.png)
*Figure 5: The SDLC lifecycle phases shown as a circular process.*

**Phases in order:**

```
Planning → Analysis → Design → Development → Testing → Deployment → Maintenance
```

---

### SDLC Models Compared

| Model | How It Works | Weakness | Best For |
|-------|-------------|----------|----------|
| **Waterfall** | Phases flow strictly in order - no going back | Rigid; cannot handle mid-project changes | Simple, well-defined projects |
| **Agile** | Small iterations (sprints) with continuous feedback | Requires active stakeholder involvement | Modern apps, startups, flexibility required |
| **Spiral** | Loops of design + risk analysis (called spirals) | Complex and expensive to manage | Large, high-risk projects |
| **V-Model** | Every dev phase has a paired testing phase | Still sequential like Waterfall | Safety-critical systems (banking, medical) |

> 💡 **Agile is preferred over Waterfall** when flexibility matters and requirements may change - which is most modern software projects.

---

### SDLC vs. CI/CD - What's the Difference?

| Aspect | SDLC | CI/CD |
|--------|------|-------|
| **Full Name** | Software Development Life Cycle | Continuous Integration & Continuous Delivery/Deployment |
| **Scope** | The entire process of building software | Automating the build, test, and deploy steps |
| **Focus** | Planning through maintenance | Integration, testing, and deployment automation |
| **Type** | Methodology / framework | DevOps automation practice |
| **Goal** | Manages the full development process | Speeds up software delivery and reduces manual work |

---

### Build vs. Develop

| Term | Definition |
|------|-----------|
| **Development** | Writing the source code |
| **Build** | Compiling/packaging code into a runnable form (e.g., a `.exe` on Windows) |

---

## 6. Linux Command Practice

Before working with Docker, foundational Linux skills are essential since most containers run Linux.

![Linux Terminal showing command prompt](images/linux-terminal.png)
*Figure 6: A Linux terminal - the primary interface for working with Docker and containers.*

### File & Directory Commands

```bash
# View directory tree structure
tree .

# Create an empty file
touch empty_file.txt

# Create and edit a file with content
nano contents_file.txt        # Save: Ctrl+X → Y → Enter

# Create an empty directory
mkdir empty_dir

# Create a nested directory structure in one command
mkdir -p asia/india/bangalore

# Copy a single file to a target directory
cp bangalore.txt /home/thor/asia/india

# Copy an entire directory recursively
cp -r /home/thor/asia/india/bangalore /home

# Remove a single file
rm /home/thor/asia/bangalore.txt

# Remove a directory and all its contents (use with caution!)
rm -rf /home/thor/asia/india/bangalore
```

### Key Flags Explained

| Flag | Command | Meaning |
|------|---------|---------|
| `-p` | `mkdir -p` | **Parent** - creates all missing parent directories automatically |
| `-r` | `cp -r`, `rm -r` | **Recursive** - applies the command to all contents inside a directory |
| `-f` | `rm -f` | **Force** - skips confirmation prompts |
| `-it` | `docker run -it` | **Interactive + TTY** - opens a live terminal session inside the container |

---

## 7. Containers vs. Virtual Machines

> *Docker is NOT virtualization. Docker shares the kernel of the host OS, while a VM runs a complete separate OS on top of a hypervisor. This single architectural difference is why containers boot in seconds and weigh megabytes instead of gigabytes.*

![Containers vs VMs architecture diagram - Docker Engine on Host OS vs Hypervisor with Guest OS per VM](images/containers-vs-vms.png)
*Figure 7: Architectural comparison - containers (left) share the host kernel while VMs (right) each run a full guest OS.*

### Feature Comparison

| Feature | Virtual Machine | Docker Container |
|---------|----------------|-----------------|
| **Boot Time** | Minutes | Seconds |
| **Size** | Gigabytes | Megabytes |
| **Operating System** | Separate Guest OS per VM | Shares host OS kernel |
| **Speed** | Slower - goes through a hypervisor | Faster - runs directly on host OS |
| **Storage** | Heavy | Light |
| **Availability** | Ready-made VMs are hard to find | Easily available on Docker Hub |
| **Movability** | Can be migrated to a new host | Destroyed and recreated from image |
| **Tooling** | Simple, easy to use | More complex but more powerful |
| **Isolation** | Strong - full OS boundary | Process-level isolation |

---

### Container vs. Image

Think of it like a **class vs. an object** in programming - the image is the class (blueprint), the container is the object (instance).

![Image spawning multiple Containers diagram](images/image-to-containers.png)
*Figure 8: One image can spawn multiple independent running containers simultaneously.*

| Feature | Container | Image |
|---------|-----------|-------|
| **Definition** | Running instance of an image | Blueprint/template to create containers |
| **State** | Active (running or stopped) | Static (read-only) |
| **Purpose** | Executes the application | Stores the app and its dependencies |
| **Modifiable** | Yes, while running | No - always read-only |
| **Creation** | Launched from an image | Built using a Dockerfile |
| **Lifecycle** | Can start, stop, restart, delete | Stored permanently unless removed |
| **Analogy** | A running program | An installation file (`.exe`, `.dmg`) |

---

## 8. Cloud Computing Service Models

Containers and cloud computing go hand-in-hand. Understanding the three service models clarifies where Docker fits.

![IaaS PaaS SaaS pyramid diagram](images/cloud-service-models.png)
*Figure 9: The three cloud service models - from most control (IaaS) to least control (SaaS).*

| Model | Full Name | You Manage | Provider Manages | Example |
|-------|-----------|-----------|-----------------|---------|
| **IaaS** | Infrastructure as a Service | OS, apps, data | Hardware, networking | AWS EC2, Azure VMs |
| **PaaS** | Platform as a Service | Your app code | OS, runtime, hardware | Google Cloud Platform, Heroku |
| **SaaS** | Software as a Service | Your data only | Everything else | Gmail, Microsoft Office 365 |

> 💡 **Docker on the cloud:** Containers run at the IaaS/PaaS layer - you bring the container, the cloud provides the infrastructure to run it.

---

## 9. Jenkins & Data Persistence

### What is Jenkins?

> *Jenkins is the leading open-source automation server used to build, test, and deploy software. It is a critical tool in DevOps for implementing CI and CD pipelines.*

Put simply: Jenkins **automatically builds, tests, and delivers your code** so you don't have to do it manually every time something changes.

> ⚠️ **Important:** Jenkins does not deploy by itself - it **orchestrates the pipeline** that leads to deployment.

![Jenkins CI/CD Pipeline - Commit → Build → Test → Stage → Deploy](images/jenkins-cicd-pipeline.png)
*Figure 10: A Jenkins CI/CD pipeline taking code from commit all the way to production.*

---

### Running Jenkins in Docker

```bash
# Launch Jenkins with port mapping
docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins:latest
```

| Flag | Meaning |
|------|---------|
| `-p 8080:8080` | Maps host port 8080 → container port 8080 (web UI) |
| `-p 50000:50000` | Maps port for Jenkins agent connections |

**Accessing the UI:** Two options:
1. Use the container's internal IP directly
2. Use port mapping and access via the host's external IP (`http://<host-ip>:8080`)

---

### Key Jenkins Terminology

| Term | Definition |
|------|-----------|
| **Plugin** | A small add-on that extends Jenkins functionality (e.g., Git plugin, Docker plugin) |
| **Pipeline** | A sequence of automated steps: build → test → deploy |
| **Snippet** | A reusable block of pipeline code |
| **Volume** | Persistent storage that lives outside the container |

---

### Container Exit Codes

When a container stops, its exit code tells you *why*:

| Exit Code | Signal | Cause |
|-----------|--------|-------|
| `0` | - | Completed successfully |
| `130` | SIGINT | Stopped using `Ctrl+C` |
| `137` | SIGKILL (9) | Force-killed via `docker kill` or out-of-memory |
| `143` | SIGTERM (15) | Graceful stop via `docker stop` |

---

### Data Persistence & Docker Volumes

> *Data persistence means storing data in a non-volatile medium so it remains intact even after an application is closed, a container is deleted, or a system fails.*

Containers are **ephemeral by design** - when you delete a container, everything inside is gone. Volumes solve this.

```bash
# Create a local directory for Jenkins data
mkdir my-jenkins-data

# Run Jenkins with a volume mounted
docker run -p 8080:8080 \
  -v my-jenkins-data:/var/jenkins_home \
  jenkins/jenkins:latest
```

| Storage Type | Persists after container deletion? | Example |
|-------------|----------------------------------|---------|
| Container filesystem | ❌ No | Logs written inside the container |
| Docker Volume | ✅ Yes | Jenkins build history, config files |
| Bind Mount | ✅ Yes | Local directory mapped into container |

---

### Networking Concepts

| Term | Definition |
|------|-----------|
| **MAC Address** | Hardware identity (Media Access Control) assigned to a network interface - unique per device |
| **Gateway** | The entry/exit point between two networks (e.g., your router between your LAN and the internet) |
| **Port Mapping** | `-p external:internal` - exposes a container port to the host |

---

## 10. Python & PIP

### What is PIP?

> *PIP is a package manager for Python - a tool that installs and manages extra Python libraries. Think of it as Python's App Store.*

**PIP** is a recursive acronym: **P**ip **I**nstalls **P**ackages.
(Other recursive acronyms: **PHP** = PHP Hypertext Preprocessor, **YAML** = YAML Ain't Markup Language)

```bash
# Install Flask using pip
python3 -m pip install flask

# Install from a requirements file (best practice)
python3 -m pip install -r requirements.txt

# List installed packages
pip list
```

> **Why `-m`?** The `-m` flag tells Python: *don't run a file - find this module inside Python and run it like a program.* Without `-m`, Python would look for a file named `pip` in the current directory.

---

### Python Concepts

| Concept | Definition |
|---------|-----------|
| **Module** | A `.py` file containing reusable functions, classes, and variables |
| **Package** | A collection of related modules |
| **Library** | A collection of packages (e.g., Flask, NumPy) |
| **Virtual Environment** | An isolated Python environment per project - avoids dependency conflicts |

---

### Array vs. List

| Feature | Array | List |
|---------|-------|------|
| Size | Fixed at creation | Dynamic - grows and shrinks |
| Data Types | One type only (e.g., all integers) | Can mix any types |
| Performance | Faster for numeric operations | More flexible and general-purpose |
| Python module needed | `array` or `numpy` | Built-in, no import needed |

---

## 11. Building a Flask Docker Image

### The End-to-End Workflow

```
Write app → Write Dockerfile → Build image → Run container → Test → Tag → Push → Share
```

![Flask Docker build workflow diagram](images/flask-docker-workflow.png)
*Figure 11: From local Flask app to a publicly accessible Docker Hub image.*

---

### The Flask Application (`app.py`)

```python
import os
from flask import Flask

app = Flask(__name__)

@app.route("/")
def main():
    return "Welcome!"

@app.route('/how are you')
def hello():
    return 'I am good, how about you?'

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=8080)
```

> **Why `host="0.0.0.0"`?** This tells Flask to listen on all network interfaces - required for Docker to route external traffic into the container. Using `localhost` or `127.0.0.1` would make the app unreachable from outside the container.

---

### The Dockerfile

```dockerfile
FROM python:3.10-slim       # Lightweight Python base image

WORKDIR /app                # Set working directory inside container

COPY . .                    # Copy all files from host into /app

RUN pip install flask       # Install Flask at build time

EXPOSE 8080                 # Declare the port the app listens on

CMD ["python", "app.py"]    # Start the app when container launches
```

---

### Building & Running

```bash
# Build the image and name it "flaskapp"
docker build -t flaskapp .

# Run the container with port mapping
docker run -p 8080:8080 flaskapp

# Run in background (detached mode)
docker run -d -p 8080:8080 flaskapp

# Check it's running
docker ps
```

**Expected HTTP responses:**
- `GET /` → `200 OK` - returns "Welcome!"
- `GET /unknown` → `404 Not Found`

---

### Tagging & Pushing to Docker Hub

```bash
# Build with your Docker Hub username/repo tag
docker build . -t yourusername/flaskapp

# Verify it runs before pushing
docker run -p 8080:8080 yourusername/flaskapp

# Log in to Docker Hub (one-time)
docker login

# Push to Docker Hub (layers uploaded separately)
docker push yourusername/flaskapp
```

> The push uploads each image layer independently. Once complete, anyone in the world can run your image with `docker pull yourusername/flaskapp`.

---

## 12. Image Optimization

### The Problem

The full `python:3.6` base image weighs **913 MB** - enormous for a tiny Flask app. It ships with build tools, documentation, and development packages that a production container never uses.

### The Solution: Use Slim or Alpine Variants

```dockerfile
# ❌ Before - full image (913 MB)
FROM python:3.6

# ✅ After - Alpine variant (51.9 MB)
FROM python:3.6-alpine
```

![Image size comparison bar chart - 913 MB vs 51.9 MB](images/image-size-comparison.png)
*Figure 12: Switching base images reduces the image size by approximately 18x.*

### Results

| Image | Base Image | Size | Reduction |
|-------|-----------|------|-----------|
| `webapp-color:latest` | `python:3.6` | 913 MB | - |
| `webapp-color:lite` | `python:3.6-alpine` | 51.9 MB | **~18x smaller** |

### Common Base Image Options (Smallest to Largest)

| Base Image | Approximate Size | Best For |
|-----------|-----------------|---------|
| `alpine` | ~5 MB | Absolute minimal footprint |
| `python:3.x-alpine` | ~50 MB | Python apps needing minimal size |
| `python:3.x-slim` | ~130 MB | Python apps needing more compatibility |
| `python:3.x` | ~900 MB | Full environment, maximum compatibility |
| `ubuntu` | ~70 MB | General-purpose Linux baseline |

> 💡 **Rule of thumb:** Start with the smallest image that works. Add layers only when something breaks. Smaller images = faster pulls, faster builds, smaller attack surface.

---

## 13. The Universal 5-Step Dockerfile Skeleton

By the end of the course, a universal pattern had emerged. Almost every Dockerfile follows this skeleton:

```
FROM → WORKDIR → COPY → RUN → CMD
  ↓       ↓        ↓      ↓      ↓
base   working  files  install  start
image    dir           deps     app
```

![5-Step Dockerfile Skeleton diagram with labeled arrows](images/dockerfile-5-step-skeleton.png)
*Figure 13: The universal Dockerfile skeleton - five steps that cover the vast majority of real-world images.*

---

### Step 1: `FROM` - The Foundation

```dockerfile
FROM python:3.10-slim
```

The **base image** is your starting point - a prebuilt environment that already has a runtime, OS utilities, or frameworks ready to go. You build on top of it rather than starting from zero.

**Common choices:**

| Base Image | Runtime |
|-----------|---------|
| `python:3.10-slim` | Python 3.10 |
| `node:18-alpine` | Node.js 18 |
| `nginx:alpine` | Nginx web server |
| `ubuntu:22.04` | Ubuntu Linux |
| `alpine:3.18` | Bare-minimum Linux |

---

### Step 2: `WORKDIR` - The Setup

```dockerfile
WORKDIR /app
```

Sets the working directory inside the container. All subsequent `COPY`, `RUN`, and `CMD` instructions execute relative to this path. It's the container equivalent of `cd /app` before every command.

---

### Step 3: `COPY` - Moving Files

```dockerfile
COPY . .
```

Transfers files from the **host** into the **container**.

| Part | Meaning |
|------|---------|
| First `.` | Source - your current directory on the host |
| Second `.` | Destination - the `WORKDIR` inside the container |

For Node.js apps with caching optimization:
```dockerfile
COPY package*.json ./    # Copy dependency manifest first
RUN npm install          # Install before copying source
COPY . .                 # Now copy the rest
```

---

### Step 4: `RUN` - The Assembly

```dockerfile
RUN pip install flask
```

Executes shell commands **at build time** - when the image is being created, not when the container starts. Use `RUN` to install dependencies, compile code, or set up the environment.

Each `RUN` instruction creates a new image layer. To keep images lean:
```dockerfile
# ✅ Combine related commands into one RUN to reduce layers
RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*
```

---

### Step 5: `EXPOSE` & `CMD` - The Operation

```dockerfile
EXPOSE 8080
CMD ["python", "app.py"]
```

| Instruction | Purpose | Timing |
|-------------|---------|--------|
| `EXPOSE` | Documents which port the container listens on | Build time (metadata only) |
| `CMD` | The default command to run when the container starts | Runtime |
| `ENTRYPOINT` | Like `CMD` but harder to override from the command line | Runtime |

> **`CMD` vs `ENTRYPOINT`:**
> - `CMD` - easily overridden: `docker run myapp python other_script.py`
> - `ENTRYPOINT` - the command is fixed; arguments can be appended

---

### Full Example: Optimized Node.js Dockerfile

```dockerfile
# Step 1: Start from a minimal Node.js image
FROM node:18-alpine

# Step 2: Set the working directory
WORKDIR /app

# Step 3a: Copy only dependency manifest first (enables layer caching)
COPY package*.json ./

# Step 3b: Install dependencies - this layer is cached if package.json hasn't changed
RUN npm install

# Step 3c: Copy the rest of the source code
COPY . .

# Step 4: Expose the app's port
EXPOSE 8080

# Step 5: Start the application
CMD ["node", "server.js"]
```

> **Why this order matters - Layer Caching:**
> Docker builds images layer by layer and caches each one. If a layer hasn't changed, Docker reuses the cache and skips rebuilding it. By copying `package.json` and running `npm install` *before* copying source code, a code-only change skips the slow `npm install` step entirely - rebuilds go from minutes to seconds.

---

## 14. Key Takeaways

| Principle | Why It Matters |
|-----------|---------------|
| **Containers share the host kernel** | Makes them seconds-fast and megabyte-light vs VMs |
| **Images are blueprints; containers are running instances** | Confusing the two leads to mistakes in every other Docker concept |
| **The 5-step skeleton covers most Dockerfiles** | Internalize `FROM → WORKDIR → COPY → RUN → CMD` and writing Dockerfiles becomes routine |
| **Base image choice dominates image size** | `python:3.6` → `python:3.6-alpine` cut size by **18x** |
| **Volumes give you persistence** | Containers are disposable - your data doesn't have to be |
| **Port mapping (`-p external:internal`)** | Without it, your service is completely invisible from outside the container |
| **Layer caching rewards careful ordering** | Copy dependency files first, install, then copy source - this alone can save minutes per build |
| **Tag with `username/repo` before pushing** | This links your local image to your Docker Hub identity |
| **Jenkins orchestrates, not deploys** | Jenkins manages the pipeline; actual deployment is a step within it |
| **`docker exec` lets you inspect live containers** | Invaluable for debugging without stopping your running service |

---

## 15. Quick Reference: Essential Docker Commands

### Container Lifecycle

```bash
docker run -it ubuntu bash           # Run interactively with a terminal
docker run -d -p 8080:8080 myapp     # Run in background with port mapping
docker run --name mycontainer myapp  # Give the container a custom name

docker ps                            # List running containers
docker ps -a                         # List ALL containers (including stopped)
docker stop <container-id>           # Graceful stop (SIGTERM, exit code 143)
docker kill <container-id>           # Force stop (SIGKILL, exit code 137)
docker restart <container-id>        # Restart a stopped container
docker rm <container-id>             # Delete a stopped container
docker rm -f <container-id>          # Force-delete a running container
```

### Inspecting Containers

```bash
docker exec <container-id> bash      # Open a shell inside a running container
docker exec <container-id> cat /etc/os-release  # Run a single command
docker logs <container-id>           # View container logs
docker inspect <container-id>        # Full JSON details (IP, mounts, config)
```

### Images

```bash
docker images                        # List all local images
docker pull ubuntu                   # Download an image from Docker Hub
docker build -t myapp .              # Build image from Dockerfile in current dir
docker build -t myapp:v2 .           # Build with a version tag
docker tag myapp username/myapp      # Tag for Docker Hub
docker push username/myapp           # Push to Docker Hub
docker rmi <image-id>                # Remove a local image
docker image prune                   # Remove all unused images
```

### Volumes & Networking

```bash
docker volume create mydata          # Create a named volume
docker run -v mydata:/app/data myapp # Mount volume into container
docker volume ls                     # List all volumes
docker volume rm mydata              # Delete a volume

docker run -p 8080:8080 myapp        # Map host port 8080 → container 8080
docker run -p 3000:8080 myapp        # Map host port 3000 → container 8080
```

### System & Cleanup

```bash
docker system df                     # Show disk usage by Docker
docker system prune                  # Remove all unused containers, images, networks
docker stats                         # Live resource usage for all running containers
```

---

## References

| Resource | Description |
|---------|-------------|
| [Docker Official Documentation](https://docs.docker.com) | All Docker commands, Dockerfile syntax, and architecture details |
| [Docker Hub](https://hub.docker.com) | Registry for pushing/pulling images - includes official Python, Node.js, Nginx base images |
| [Jenkins Documentation](https://www.jenkins.io/doc/) | Official guide to Jenkins pipelines, plugins, and CI/CD setup |
| [KodeKloud](https://kodekloud.com) | Hands-on Docker and DevOps labs (used for webapp-color exercise) |
| [Flask Documentation](https://flask.palletsprojects.com) | Flask micro-framework reference |
| [Alpine Linux](https://alpinelinux.org) | The minimal Linux distribution behind slim base images like `python:3.x-alpine` |

---

*Notes compiled from: DevOps & Docker: Containerization, CI/CD, and Modern Deployment Practices - DRAC Blog, May 2026*

