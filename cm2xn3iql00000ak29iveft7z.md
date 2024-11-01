---
title: "Introductory Docker Guide: Easy Steps to Begin"
seoTitle: "Beginner's Docker Guide: Simple Start Steps"
seoDescription: "Learn Docker basics with this introductory guide, covering key features, commands, and Dockerfile usage to enhance your development workflow"
datePublished: Thu Oct 31 2024 18:29:14 GMT+0000 (Coordinated Universal Time)
cuid: cm2xn3iql00000ak29iveft7z
slug: introductory-docker-guide-easy-steps-to-begin
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1730440172791/dbea8d4b-75f7-4650-8fe8-c87db5fd5e64.png
tags: linux, docker, devops, docker-images, 90daysofdevops

---

## What is Docker?

Docker is an open-source platform designed for automating the deployment, scaling, and management of applications in lightweight, portable containers. These containers bundle applications with all their dependencies, ensuring that they run consistently across various environments—whether on a developer's laptop or in a cloud-based production environment.

### Key Features of Docker

1. **Containerization**: Docker encapsulates applications and their dependencies into isolated containers, eliminating conflicts between applications.
    
2. **Portability**: Docker containers can run on any system with Docker installed, making it easy to develop once and deploy anywhere.
    
3. **Efficiency**: Containers share the host OS kernel, making them lighter and faster than traditional virtual machines (VMs), which include their own OS.
    
4. **Scalability**: Docker allows for quick scaling of applications by rapidly spinning up or shutting down containers.
    
5. **Version Control**: Docker images can be versioned, making it easier to manage different application versions.
    
6. **CI/CD Integration**: Docker integrates seamlessly with continuous integration and continuous deployment (CI/CD) tools, facilitating automated testing and deployment.
    

## Containerization vs. Virtualization

While both containerization and virtualization provide isolation for applications, they do so differently.

### Virtualization

* **Architecture**: Virtualization creates multiple virtual machines (VMs) on a single physical host, each with its own OS and applications.
    
* **Resource Overhead**: Each VM consumes significant resources due to the full OS and hypervisor, leading to slower performance.
    
* **Isolation**: VMs offer strong isolation, making them suitable for running different OS types or meeting strict compliance needs.
    

### Containerization

* **Architecture**: Containerization runs applications in isolated user spaces on a shared OS kernel, resulting in a lightweight approach.
    
* **Resource Efficiency**: Containers have lower resource overhead, leading to faster startup times and improved performance.
    
* **Isolation**: While containers provide a good level of isolation, they share the host kernel, which can raise security concerns.
    
* **Use Cases**: Ideal for microservices architectures, rapid development, and scenarios requiring efficient resource use.
    

## Basic Docker Commands

Here are some essential Docker commands to help you get started, along with examples and use cases.

### 1\. Installing Docker

To get started with Docker, first install it on your machine. You can find installation instructions for various operating systems on the Docker website.

### 2\. Basic Commands

* #### `docker --version`
    

Check the installed Docker version.

```bash
docker --version
```

* #### `docker pull`
    

Download a Docker image from Docker Hub.

```bash
docker pull nginx
```

**Use Case**: Download the Nginx web server image for use in a web application.

* #### `docker images`
    

List all downloaded images.

```bash
docker images
```

* #### `docker run`
    

Create and start a container from an image.

```bash
docker run -d -p 80:80 nginx
```

The docker run`-d (detached mode)` the -d runs in the background, leaving the terminal clear.

**Use Case**: Start an Nginx container in detached mode, mapping port 80 of the container to port 80 on the host.

* `docker run -dit`
    

```bash
docker run -dit
```

The `-dit` means it runs the container in detached mode and gives an interactive terminal.

* #### `docker ps`
    

List all running containers.

```bash
docker ps
```

* `docker ps -a`
    

List all the running and stop containers.

```bash
docker ps -a
```

* #### `docker stop`
    

Stop a running container.

```bash
docker stop <container_id>
```

**Use Case**: Stop the Nginx container when it’s no longer needed.

> We can use docker kill &lt;container\_id&gt; to kill the container immediately.

* #### `docker rm`
    

Remove a stopped container.

```bash
docker rm <container_id>
```

* #### `docker rmi`
    

Remove an unused image.

```bash
docker rmi nginx
```

**Use Case**: Clean up unused images after development or testing.

* `docker exec -it`
    

```bash
docker exec -it <container_name> bash
```

The command `docker exec -it <container_name> <command>` is used to run a command in a running container.

* `docker logs`
    

```bash
docker logs <container_name>
```

The `docker logs <container_name>` command is used to fetch and display the logs generated by a running or stopped container.

**Common Prune Commands**

The `docker prune` command is used to remove unused data from Docker, helping to free up space.

* Remove Unused Containers.
    

```bash
docker container prune
```

This command removes all the stopped containers.

* **Remove Unused Images**:
    
    ```bash
    docker image prune
    ```
    
    This command removes dangling images (those not tagged or associated with a container). You can also use the `-a` flag to remove all unused images, not just dangling ones:
    
    ```bash
    docker image prune -a
    ```
    
* **Remove Unused Networks**:
    
    ```bash
    docker network prune
    ```
    
    This command removes networks that are not used by any containers.
    
* **Remove Unused Volumes**:
    
    ```bash
    docker volume prune
    ```
    
    This command removes all unused volumes.
    
* **Prune All Unused Objects**: You can use the `docker system prune` command to remove all unused data (stopped containers, dangling images, unused networks, and build cache) in one go:
    
    ```bash
    docker system prune
    ```
    
    You can also add the `-a` flag to remove all unused images and not just dangling ones:
    
    ```bash
    docker system prune -a
    ```
    

> **Caution:** Pruning is irreversible, so be sure you want to delete the unused data before running these commands, as you may lose important resources if they are not backed up or are still in use elsewhere.

3\. Working with Dockerfiles

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1730440318187/90993aed-741d-4218-9581-4b310af1cc51.png align="center")

A Dockerfile is a text file that contains instructions for building a Docker image. Here’s a simple example:

```dockerfile
# Use the official Node.js image as a base
FROM node:14

# Set the working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package.json ./
RUN npm install

# Copy the rest of the application
COPY . .

# Expose the application port
EXPOSE 3000

# Command to run the application
CMD ["node", "server.js"]
```

To build and run the Docker image defined by the Dockerfile:

```bash
docker build -t my-node-app .
docker run -d -p 3000:3000 my-node-app
```

**Use Case**: Deploy a Node.js application using a custom Dockerfile.

### 4\. Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications. Here’s a simple `docker-compose.yml` example:

To start the application with Docker Compose:

```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "80:80"
  db:
    image: postgres
    environment:
      POSTGRES_PASSWORD: example
```

```bash
docker-compose up
```

**Use Case**: Launch a web application with an Nginx front-end and a PostgreSQL database.

## Conclusion

Docker has transformed application development and deployment by providing a powerful containerization platform. By understanding the basics of Docker commands and how to work with images and containers, you can streamline your development processes and ensure consistency across environments. Whether you're building microservices or managing complex applications, Docker offers the flexibility and efficiency needed to succeed in today's fast-paced development landscape.

---

Thank you for reading! 🚀 If you found this guide helpful or have any suggestions, tips, or questions about Linux Permissions, please feel free to leave a comment below. I’d love to hear from you and learn together!

Don't forget to follow my blog for more awesome insights on development topics, and connect with me on [LinkedIn](https://www.linkedin.com/in/ahireshubham/) and [GitHub](https://github.com/Shubham-Ahire) to stay updated on all things tech and coding! 🎉