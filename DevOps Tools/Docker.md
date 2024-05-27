# Introduction

## Basic Concepts

- **Image**: A lightweight, standalone, executable package that includes everything needed to run a piece of software, including the code, runtime, libraries, and environment variables.
- **Container**: A runtime instance of an image. It is a lightweight and portable encapsulation of an environment in which to run applications.
- **Dockerfile**: A text document that contains all the commands to assemble an image.
- **Docker Hub**: A cloud-based repository in which Docker users and partners create, test, store, and distribute container images.

## Common Commands

### Docker Installation

#### On Ubuntu
```
sudo apt-get update
sudo apt-get install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
```
## Docker Version
```
docker --version
```
## Docker Help
```
docker --help
```

# Working with Docker Images

## List Docker Images
```
docker images
```

## Pull an Image from Docker Hub
```
docker pull <image_name>
# Example:
docker pull ubuntu
```

## Build an Image from Dockerfile
```
docker build -t <image_name> .
# Example:
docker build -t my_app .
```

## Remove an Image
```
docker rmi <image_id>
# Example:
docker rmi d0e008c6cf02
```

# Working with Docker Containers

## List Running Containers
```
docker ps
```

## List All Containers (including stopped ones)
```
docker ps -a
```

## Run a Container
```
docker run <image_name>
# Example:
docker run ubuntu
```

### Run a Container with Interactive Terminal
```
docker run -it <image_name> /bin/bash
# Example:
docker run -it ubuntu /bin/bash
```

## Run a Container in Detached Mode
```
docker run -d <image_name>
# Example:
docker run -d ubuntu
```

## Stop a Running Container
```
docker stop <container_id>
# Example:
docker stop 5d3b1b7e7f0d
```

## Remove a Stopped Container
```
docker rm <container_id>
# Example:
docker rm 5d3b1b7e7f0d
```

## Remove All Stopped Containers
```
docker container prune
```

# Dockerfile Instructions

## Basic Dockerfile Example
```
# Use an official Python runtime as a parent image
FROM python:3.8-slim-buster

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```

## Build an Image from Dockerfile
```
docker build -t <image_name> .
# Example:
docker build -t my_python_app .
```

# Docker Compose

## docker-compose.yml Example
```
version: '3'
services:
  web:
    image: nginx
    ports:
      - "80:80"
  redis:
    image: "redis:alpine"
```

## Start Services
```
docker-compose up
```

## Stop Services
```
docker-compose down
```

# Docker Networking

## List Networks
```
docker network ls
```

## Create a Network
```
docker network create <network_name>
# Example:
docker network create my_network
```

## Connect a Container to a Network
```
docker network connect <network_name> <container_id>
# Example:
docker network connect my_network 5d3b1b7e7f0d
```

## Disconnect a Container from a Network
```
docker network disconnect <network_name> <container_id>
# Example:
docker network disconnect my_network 5d3b1b7e7f0d
```

# Docker Volumes

## List Volumes
```
docker volume ls
```

## Create a Volume
```
docker volume create <volume_name>
# Example:
docker volume create my_volume
```

## Mount a Volume to a Container
```
docker run -v <volume_name>:/path/in/container <image_name>
# Example:
docker run -v my_volume:/data ubuntu
```

# Docker Swarm

## Initialize a Swarm
```
docker swarm init
```

## Join a Swarm
```
docker swarm join --token <token> <manager_ip>:<port>
# Example:
docker swarm join --token SWMTKN-1-4f8a0yue7t6x 192.168.0.1:2377
```

## List Nodes in a Swarm
```
docker node ls
```

## Deploy a Stack
```
docker stack deploy -c <compose-file> <stack_name>
# Example:
docker stack deploy -c docker-compose.yml my_stack
```

## List Stacks
```
docker stack ls
```

## Remove a Stack
```
docker stack rm <stack_name>
# Example:
docker stack rm my_stack
```

# Resources

[Docker Documentation](https://docs.docker.com/reference/)

This cheat sheet provides a comprehensive overview of Docker, covering basic concepts, common commands, Dockerfile instructions, Docker Compose, networking, volumes, and Docker Swarm.
