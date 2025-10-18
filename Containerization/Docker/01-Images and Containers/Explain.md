# Explain

# Images

## Images properties

- A **Docker image** is like a **blueprint** or **template**.
- It contains everything your app needs to run:
    - OS (minimal version, e.g., Ubuntu)
    - App code
    - Dependencies
    - Configurations
- **Images are read-only**. You don’t run code directly inside an image; you use it to create containers.
- The images can be built with all its environment variables and take it to run a container on any needed machine
    - This solved problem of APP is working on machine and not working in another one
- Images have 2 states
    - **Build_time**: executed when image is being built [ install software, configure file system…]
    - **Run_time**:  commands that are being executed at running the container
- Images are pulled from **registry**
    - Saved then i can run container anytime
    - Or if i run the container and image isn’t saved → it will be pulled automatically
    - The default registry is **Docker hub**
    - Registry has a lot of repos, each repo has all versions of one image, each image’s version called **Tag** → <image name> = **<repo>:<tag>**
    - If repo is unofficial → <image name> = <acc>/<repo>:<tag>
- If there’s common layers between images it ‘ll not download the whole image from scratch → it will use the common layers and then pull the new ones
- Each image has manifest file

### Manifest file

Is basically a **metadata file** (usually in JSON format) that describes what’s inside the image and how it should be run.

- **Image configuration reference**
    - Points to another JSON file (the image config) that contains:
        - Entrypoint / CMD
        - Environment variables
        - Working directory
        - OS and architecture info (e.g., `linux/amd64`)
- **List of layers**
    - SHA256 digests of all the tar files that make up the filesystem layers of the image.
- **Media types**
    - Specifies the type of content (like Docker schema v2 format).
- **Platform information**
    - Architecture and operating system.

# Containers

- A **container** is a **running instance of an image**.
- When you start a container from an image, Docker:
    - Takes the image (read-only).
    - Adds a thin **writable layer** on top.
    - Runs it as an isolated process on your host machine.

![Docker.drawio.png](images/Docker.drawio.png)

- The containers usually are used to do one task or one process
- This process will take PID=1
- If this process is exited the whole container will be exited even if the container has only the distro → the bash will take PID=1

## Types of containers

- Linux → Linux containers
- Windows
    - Windows containers
    - Linux containers by Hyper-V on Linux VM

# Engine Architecture

![7.png](images/7.png)

### 1. **Docker Client**

- CLI tool you use to run Docker commands.
- Sends requests to the Docker daemon via REST API

### 2. **Docker Daemon**

- Core service that manages Docker objects (images, containers, volumes, networks).
- Parses client commands and delegates tasks to **containerd**.
- Runs in the background as a system service.

### 3. **containerd**

- A container runtime that handles container lifecycle:
    - Pulling images
    - Managing storage (snapshots)
    - Starting/stopping containers
- Used by Docker and Kubernetes.
- Interacts with runc to actually run containers.

### 4. **runc**

- Low-level runtime responsible for creating and running containers.
- Uses **Linux kernel features**:
    - Namespaces
    - cgroups
    - seccomp
- Launches containers as actual Linux processes.