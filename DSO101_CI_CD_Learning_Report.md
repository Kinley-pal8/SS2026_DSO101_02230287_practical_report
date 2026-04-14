# DSO-101: CI/CD Module - Learning Report

**Course:** DSO-101 CI/CD  
**Date:** April 2026  
**Topic:** Containerization with Docker, Docker Compose, and Docker Optimization

---

## Table of Contents

1. Introduction
2. Executive Summary
3. Unit I: Containerization with Docker
4. Unit II: Docker Compose and Multi-Container Applications
5. Unit III: Docker Optimization & Registry
6. Key Concepts and Learnings
7. Conclusion

---

## 1. Introduction

The DSO-101 module on Continuous Integration/Continuous Deployment (CI/CD) provides comprehensive training on containerization technologies, specifically focusing on Docker and related tools. The curriculum is structured to equip learners with practical skills in building, deploying, and managing containerized applications. This report documents the learning journey through the three main units of the course, covering foundational concepts through advanced optimization techniques.

---

## 2. Executive Summary

The DSO-101 module covers three critical areas of modern DevOps practices:

- **Unit I** establishes foundational Docker knowledge, including containerization concepts, Docker architecture, and practical CLI operations
- **Unit II** extends this knowledge to orchestration using Docker Compose, enabling the management of complex multi-container applications
- **Unit III** addresses production-level concerns including image optimization and registry management

Together, these units provide a structured pathway from basic containerization to enterprise-ready deployment practices.

---

## 3. Unit I: Containerization with Docker

### 3.1 Introduction to Docker

#### 3.1.1 Containerization Concepts

The course introduces containerization as a lightweight virtualization approach that packages applications with all their dependencies into isolated environments. Key concepts include:

- **Containers** as standalone, executable units that ensure consistency across development, testing, and production environments
- **Images** as blueprints or templates that define the container environment
- **Isolation** mechanisms that ensure containers run independently without interfering with one another
- **Portability** as a core benefit, allowing containers to run consistently on any system with Docker installed

#### 3.1.2 Docker Architecture

Understanding Docker's architecture is fundamental to effective container management:

- **Docker Daemon** - Background service that manages containers and images
- **Docker Client** - Command-line interface for user interaction with the daemon
- **Docker Images** - Read-only templates containing all necessary components
- **Docker Containers** - Runtime instances of images with writable layers
- **Docker Registry** - Centralized storage for sharing images
- **Layered Filesystem** - Union file system approach enabling efficient storage

#### 3.1.3 Docker vs. Virtual Machines

A critical distinction in the course:

| Aspect              | Docker Containers               | Virtual Machines                   |
| ------------------- | ------------------------------- | ---------------------------------- |
| **Overhead**        | Minimal, shares host OS kernel  | Significant, includes full OS      |
| **Boot Time**       | Seconds                         | Minutes                            |
| **Resource Usage**  | Lightweight, efficient          | Heavier, more resource-intensive   |
| **Isolation Level** | Process-level isolation         | Hardware-level isolation           |
| **Use Case**        | Microservices, rapid deployment | Complete OS isolation, legacy apps |

### 3.2 Working with Docker

#### 3.2.1 Installing Docker

The module covers:

- Platform-specific installation procedures (Linux, Windows, macOS)
- Post-installation verification and configuration
- Docker Desktop variant for local development
- Docker Engine for production deployments

#### 3.2.2 Docker CLI Basics

Essential commands covered include:

- `docker run` - Creating and running containers from images
- `docker ps` - Listing active containers
- `docker images` - Viewing available images
- `docker pull` - Downloading images from registries
- `docker build` - Creating custom images
- `docker stop/start` - Managing container lifecycle
- `docker logs` - Accessing container output
- `docker exec` - Running commands inside containers

#### 3.2.3 Pulling and Running Docker Images

Practical experience with:

- Authenticating with Docker registries
- Pulling pre-built images from Docker Hub
- Running containers with port mapping and environment variables
- Container naming and identification
- Interactive and detached mode execution

### 3.3 Building Docker Images

#### 3.3.1 Dockerfile Syntax

The course covers the fundamental Dockerfile instructions:

- `FROM` - Specifies the base image
- `RUN` - Executes commands during build
- `COPY/ADD` - Transfers files into the image
- `WORKDIR` - Sets the working directory
- `CMD` - Defines default container command
- `ENTRYPOINT` - Specifies the container's entry point
- `ENV` - Sets environment variables
- `EXPOSE` - Documents opened ports

#### 3.3.2 Building Custom Images

Practical skills developed:

- Creating Dockerfiles for various application types
- Multi-language application containerization
- Build context management
- Build arguments and variable substitution
- Managing build cache for optimal compilation times

#### 3.3.3 Best Practices for Dockerfile Creation

Critical practices for production-ready images:

- **Minimizing layers** - Combining commands to reduce image size
- **Using specific base image versions** - Avoiding latest tags for reproducibility
- **Separating build and runtime** - Using multi-stage builds to reduce final image size
- **Not running as root** - Creating dedicated user accounts for security
- **Ordering instructions efficiently** - Placing frequently changing instructions at the end
- **Using .dockerignore** - Excluding unnecessary files from context
- **Keeping images lightweight** - Installing only required dependencies

### 3.4 Docker Networking

#### 3.4.1 Docker Network Types

The module explores three primary network types:

- **Bridge Networks** - Default network, suitable for standalone containers with limited communication
- **Host Networks** - Container shares host network stack, eliminating network isolation
- **Overlay Networks** - For multi-host container communication in Docker Swarm

#### 3.4.2 Creating and Managing Docker Networks

Practical operations include:

- Creating custom bridge networks
- Assigning containers to specific networks
- Naming resolution within networks
- Port publishing and mapping
- Network inspection and debugging

#### 3.4.3 Container-to-Container Communication

Key learnings:

- Automatic DNS resolution between containers on the same network
- Service discovery through container names
- Load balancing across multiple container instances
- Network isolation between separate networks
- Exposing ports for external access

### 3.5 Docker Volumes

#### 3.5.1 Understanding Docker Storage Drivers

Storage architecture fundamentals:

- **AUFS, overlay2, and other drivers** - Layered filesystem implementations
- **Copy-on-Write (CoW)** - Mechanism for efficient storage of container changes
- **Storage performance implications** - Driver selection impact on performance
- **Cross-platform considerations** - Storage driver availability on different systems

#### 3.5.2 Creating and Managing Volumes

Volume operations covered:

- Creating named volumes for persistent data
- Mounting volumes in containers
- Volume driver selection
- Backup and restore procedures
- Volume inspection and cleanup

#### 3.5.3 Persisting Data with Volumes

Practical scenarios:

- Database data persistence
- Configuration file management
- Log file aggregation
- Sharing data between containers
- Volume lifecycle management

---

## 4. Unit II: Docker Compose and Multi-Container Applications

### 4.1 Introduction to Docker Compose

#### 4.1.1 Docker Compose File Structure

The course covers YAML-based configuration:

- **Services** - Application components definition
- **Networks** - Inter-service communication setup
- **Volumes** - Persistent storage allocation
- **Version specification** - Compose file format version
- **Top-level configuration keys** - Overall application settings

#### 4.1.2 Defining Services, Networks, and Volumes

Detailed learning on:

- Service definitions with images, ports, and environment variables
- Custom network creation for service isolation
- Volume attachment and management
- Dependency ordering between services
- Service health checks and restart policies

### 4.2 Managing Multi-Container Applications

#### 4.2.1 Creating a Multi-Container Application

Practical project work involving:

- Designing application architecture with multiple services
- Coordinating interdependent services
- Managing data flow between containers
- Handling service initialization sequences
- Real-world multi-tier application examples (e.g., web server, database, cache)

#### 4.2.2 Scaling Services with Docker Compose

Scalability practices:

- Deploying multiple instances of a service
- Load balancing across service instances
- Resource constraints per service
- Horizontal scaling strategies
- Performance monitoring during scaling operations

#### 4.2.3 Compose File Versions and Compatibility

Important concepts:

- Version 2 features and limitations
- Version 3 enhancements for Docker Swarm
- Version 3.8+ features for modern deployments
- Backward compatibility considerations
- Choosing appropriate versions for target environments

### 4.3 Docker Compose in Development Environments

#### 4.3.1 Local Development with Docker Compose

Development workflow optimization:

- Rapid environment setup and teardown
- Consistent development environment replication
- Volume mounting for live code changes
- Environment-specific configuration files
- Simplified local testing with production-like infrastructure

#### 4.3.2 Debugging Applications in Containers

Debugging techniques:

- Accessing container logs and streams
- Interactive debugging with `docker-compose exec`
- Port forwarding for local connectivity
- Variable inspection and state examination
- Integration with local debugging tools

#### 4.3.3 Compose Overrides for Different Environments

Configuration management:

- Base Compose file for shared configuration
- Environment-specific override files
- Development vs. staging vs. production configurations
- Secret management across environments
- Dynamic configuration based on environment variables

### 4.4 Docker Compose Best Practices

#### 4.4.1 Organizing Compose Files

Structural best practices:

- Logical grouping of related services
- Clear naming conventions for services and volumes
- Documentation through comments
- Modularization for complex applications
- Version control considerations

#### 4.4.2 Environment Variables and Secrets Management

Security and flexibility practices:

- Using `.env` files for configuration
- Variable substitution in Compose files
- Secrets storage for sensitive information
- Principle of least privilege
- Avoiding hardcoded credentials in repositories

#### 4.4.3 Health Checks and Dependency Management

Reliability practices:

- Defining health check procedures
- Startup order management with `depends_on`
- Wait strategies for service readiness
- Automatic restart policies
- Graceful shutdown handling

---

## 5. Unit III: Docker Optimization & Registry

### 5.1 Optimizing Docker Images

#### 5.1.1 Multi-Stage Builds

Advanced image optimization technique:

- Separating build and runtime environments
- Reducing final image size significantly
- Using intermediate images for compilation
- Selective artifact copying
- Application-specific optimization patterns

Example scenario: Building a Go application where the build stage is heavy but the runtime stage is minimal, resulting in dramatically smaller production images.

#### 5.1.2 Reducing Image Size and Layers

Size optimization strategies:

- Combining RUN commands to reduce layer count
- Selecting lightweight base images (Alpine, distroless, scratch)
- Removing build artifacts and temporary files
- Using `.dockerignore` effectively
- Analyzing layer contents with `docker history`
- Compression techniques for distribution

#### 5.1.3 Caching Strategies for Faster Builds

Build performance optimization:

- Understanding Docker layer caching
- Arranging instructions for optimal cache utilization
- Cache invalidation and busting
- BuildKit advanced caching features
- Parallel build optimization

### 5.2 Working with Docker Registries

#### 5.2.1 Docker Hub and Private Registries

Registry landscape:

- Docker Hub as default public registry
- Docker Hub access and authentication
- Private registries for proprietary images (Harbor, Nexus, GitLab Registry)
- On-premises registry deployment
- Registry security and access control

#### 5.2.2 Pushing and Pulling Images

Registry operations:

- Tagging images for registry compatibility
- Authenticating with registry credentials
- Pushing images to public and private registries
- Pulling from multiple registry sources
- Handling registry authentication across teams

#### 5.2.3 Image Tagging Strategies

Professional tagging practices:

- **Version tags** - Semantic versioning (e.g., v1.2.3)
- **Latest** - Convenience tag with implications
- **Branch tags** - Branch-based image identification
- **Commit hash tags** - Traceability to source code
- **Environment tags** - Development, staging, production indicators
- **Tag immutability** - Preventing accidental overwrites

---

## 6. Key Concepts and Learnings

### 6.1 Core Docker Principles

- **Containerization** provides consistency and reproducibility
- **Isolation** through containers enables safe concurrent execution
- **Layering** enables efficient storage and fast deployment
- **Statelessness** in containers promotes scalability
- **Orchestration** through Compose enables complex deployments

### 6.2 Development Workflow Integration

- Docker accelerates development cycles through environment consistency
- Compose eliminates "works on my machine" problems
- Volume mounting enables rapid iteration
- Multi-container applications enable realistic local testing

### 6.3 Production-Ready Practices

- Image optimization reduces deployment size and time
- Registry management enables version control for infrastructure
- Tagging strategies provide traceability and rollback capabilities
- Compose best practices ensure maintainable infrastructure code

### 6.4 Future Learning Paths

The foundation established by this module enables advancement into:

- **Kubernetes** - Container orchestration at enterprise scale
- **CI/CD Pipelines** - Automated image building and deployment
- **Microservices Architecture** - Distributed application design
- **DevOps Practices** - Infrastructure as Code principles

---

## 7. Conclusion

The DSO-101 CI/CD module provides a comprehensive introduction to Docker, the industry-leading containerization platform. Through three carefully structured units, the course progresses from fundamental containerization concepts to production-level optimization and distribution practices.

**Key Takeaways:**

1. **Docker revolutionizes application deployment** by solving the consistency problem through containerization
2. **Docker Compose simplifies complex multi-container applications**, making orchestration accessible for development teams
3. **Optimization techniques** are essential for production deployments to reduce resource consumption and deployment times
4. **Registry management and tagging strategies** provide the governance layer necessary for enterprise Docker adoption
5. **These skills form the foundation** for modern DevOps practices and container-based infrastructure

The practical knowledge gained through this module - from writing Dockerfiles to managing multi-container applications - provides immediately applicable skills in modern software development environments. As containerization becomes increasingly central to software delivery, the competencies developed in DSO-101 represent essential knowledge for any infrastructure, DevOps, or backend engineer.

---

## Additional Notes for Learning

### Recommended Practice Activities

- Build and optimize Dockerfiles for various application types
- Create a multi-tier application using Docker Compose
- Push images to Docker Hub with proper tagging
- Experiment with multi-stage builds and image size reduction

### Important Resources

- Official Docker documentation: https://docs.docker.com/
- Docker Hub: https://hub.docker.com/
- Docker Best Practices: https://docs.docker.com/develop/develop-images/dockerfile_best-practices/

