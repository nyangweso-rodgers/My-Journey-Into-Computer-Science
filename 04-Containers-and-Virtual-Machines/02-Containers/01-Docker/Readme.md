# Docker

## Table Of Contents

# Introduction to Docker

- **Docker** is the most popular technology to run containers. It is a software containerization platform which allows developers to package their applications into **containers**, which can then be run on any machine that has **Dockers** installed. This makes it easier for developers to move their applications between different environments, such as **development**, **testing**, and **production**.
- **Docker** has become so popular that when the word **container** is mentioned, it is automatically assumed docker will be used to manage it.

# Why Docker?

- **Docker** is an open source tool that uses **containers** to create, deploy, and manage distributed applications.
- Many organizations now opt to use **Docker** over **VMs** because of the performance benefits that it offers.
- **Remarks**:

  - A misconception among many people is that **Docker** created the concept of **containers** but that is wrong, **Docker** only brought it to critically acclaimed status. **Containers** existed very well before **Docker**.

  - **Docker** has many different tools and technologies such as [docker hub](), [docker engine](), [docker desktop]() etc. But when we’re talking about Kubernetes and Docker, there is only one tool that we’re interested in; and that’s known as [Docker Swarm]().

# Use Cases of Docker

- Three most essential use cases of Docker:

  1. Run a database locally using docker
  2. run your application locally and in production using Docker, and
  3. run automated tests using a dockerized database,

- Using Docker, you can start many types of databases in seconds. By searching, [hub.docker.com](https://hub.docker.com/) you can find ready-to-use containers for many databases.

# Installing Docker

- Install Docker engine for windows, linux or mac OS from the [official Docker website](https://www.docker.com/)

## Install Docker Desktop

- **Docker Desktop** can be used to see which containers are running, manage containers, and perform other Docker-related tasks.
- [Install Docker Desktop on Windows](https://docs.docker.com/desktop/install/windows-install/)

# Docker Concepts

- The **Dockerfile** is the base for an **image**, and an **image** is used to create a **container**. A **container** is running as a process on the host machine. Yet, it has its own file system and is separated from the other processes.

## Two Important Docker Concepts

- At its core, **Docker** has two concepts that are useful to understand: the `Dockerfile` and **Docker Images**.

### Docker Concept #1: `Dockerfile`

- A `Dockerfile` is a text file contains the set of instructions for building a **Docker Image**.
- The first step in using **Docker** is writing a `Dockerfile`. It is an essential blueprint for constructing **Docker images**.
- Each line in this file represents a new instruction, forming a stack of layers. Each layer is cache-able. When you build an image twice, it will use the cache. When you change a line in the file, it rebuilds all instructions after and including the change.
- We use a plain text to create a `Dockerfile`.Create a new file in your current working directory called `Dockerfile`. **Components** include:

  1. `FROM:`- for a base image the command must be on top of the docker
  2. `RUN:` To execute Command, it will create a layer in the image.
  3. `MAINTAINER`: Author/owner/description
  4. `COPY:` Copy files from the local system (docker VM) we need to provide a source, destination(We cant download file from the internet and any remote directory)
  5. `ADD:` Similar to `copy` but, it provides a feature to download files from the internet, also we extract files at the docker image side.
  6. `EXPOSE:` - To Expose ports such as port 80 for Nginx, etc.
  7. `WORKDIR:` To set a working directory for a container.
  8. `CMD:` Execute commands but during container creation
  9. `ENTRYPOINT:` Similar to `CMD`, but has higher priority over `CMD`, first commands will be executed by `ENTRYPOINT` only.
  10. `ENV:`- Environment Variables

- Example:
  - Define Python Docker Container with `Dockerfile`

### Docker Concept #2: Docker Image

- A **Docker Image** serves as a template for creating **Docker Containers**. It contains all the necessary code, runtime, system tools, libraries, and settings required to run a software application.
- So, a `Dockerfile` is used to build a **Docker Image** which is then used as the template for creating one or more **Docker containers**.
- Once created, **Docker images** are immutable, meaning they cannot be changed. If you need to make changes to an application, you need to modify the `Dockerfile` and create a new image. This immutability ensures consistency and reproducibility in application deployment.

## Other Docker Concepts

### Docker Concept #3: Docker Container

- This is a dynamic, running instance of a **Docker image**. An executed image spawns a container with the command in the `Dockerfile`.
- **Remarks**:

  - one image can give life to many containers.
  - If Linux is your OS, the **Docker container** will run as a process on the host machine. If you have a Windows or macOS machine, docker will run in a VM.
  - The container will use the same kernel, either the kernel of Linux or the VM on Windows or macOS.
  - The container itself is not a virtual machine. The container cannot see other processes of the host and has its own file system. This is why it seems as it is a virtual machine. But in reality, it shares the kernel of the host machine (or the kernel of the VM).

## Docker Concept #6: Docker Registry

- A **Docker registry** is a repository for the storage and distribution of **Docker images**. **Docker registry** allows users to "pull" or "push" **Docker images**.
- [Docker Hub](https://hub.docker.com/) is the official docker registry.

## Docker Concept 7: Ports (Publishing and Exposing Ports)

- **Publishing** a port provides the ability to break through a little bit of networking isolation by setting up a forwarding rule. As an example, you can indicate that requests on your host’s port `8080` should be forwarded to the container’s port `80`.
  - `HOST_PORT`: The port number on your host machine where you want to receive traffic
  - `CONTAINER_PORT`: The port number within the container that's listening for connections
- Examples:
  - Using **Docker Compose**:
    ```yml
    services:
      app:
        image: my-image
        ports:
          - 8080:80
    ```
    - Here,
      - We are using the `HOST_PORT:CONTAINER_PORT` mapping

## Docker Concept #7: Docker Hub

- [Docker Hub](https://hub.docker.com/) is a centralized repository for storing and sharing **Docker images**. All the components required to run an application are included in a **docker image**, which serves as the container's architectural blueprint.

# Bonus

## Docker Image Best Practices

- To ensure optimal performance, scalability, and security, it’s essential to follow best practices when creating and managing **Docker images**.

### Choose the Right Base Image

- Consider using official images from trusted sources like Docker Hub, as they are regularly updated and maintained by the community.
- Choose a minimalistic base image to reduce the attack surface and optimize the image size. Alpine Linux is a popular choice for its lightweight nature.
  ```Dockerfile
    FROM Alpine:latest
  ```

### Use `.dockerignore`

- Similar to `.gitignore`, a `.dockerignore` file allows you to specify files and directories to exclude from the build context.
- By preventing unnecessary files from being added to the image, you can further reduce its size. Common exclusions include `node_modules`, `.git`, and temporary files.
  ```dockerignore
    node_modules
    .git
    *.log
  ```

# Resources

1. [docs.docker.com/guidesdocker-concepts - publishing-ports](https://docs.docker.com/guides/docker-concepts/running-containers/publishing-ports/)
2. [The Ultimate Docker Cheat Sheet](https://devopscycle.com/blog/the-ultimate-docker-cheat-sheet/?mkt_tok=NzkwLVNTQi0zNzUAAAGQiPdekjcDh3HVPGYJIzKB936CcoVM7WS2-TQr3Wh-9d0C3MLx8CwcrTfclpj6x8ue3hxOgCkcdRFkS-q9Yez85eZwMUXWRpiVsJsFJlFiW04)
3. [How to Build Docker Image : Comprehensive Beginners Guide](https://devopscube.com/build-docker-image/)
4. [What Is Docker and How Does It Work? – Docker Explained](https://www.hostinger.in/tutorials/what-is-docker)
5. [freecodecamp - How Docker Containers Work – Explained for Beginners](https://www.freecodecamp.org/news/how-docker-containers-work/)
6. [Optimize Your Deployments: Docker Image Best Practices](https://www.javacodegeeks.com/2024/01/optimize-your-deployments-docker-image-best-practices.html?ref=dailydev)
7. [Introduction to Docker Compose](https://www.baeldung.com/ops/docker-compose)
