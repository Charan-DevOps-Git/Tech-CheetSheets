# Docker Commands

## Images and Containers

- docker build -t [image_name] .: Build an image from a Dockerfile.
- docker pull [image]: Pull an image from a registry.
- docker run [image]: Run a container from an image.
- docker run -d [image]: Run a container in detached mode.
- docker run --name [container_name] [image]: Run a container with a specified name.
- docker run -p [host_port]:[container_port] [image]: Run a container with port forwarding.
- docker ps: List running containers.
- docker ps -a: List all containers.
- docker stop [container_id]: Stop a running container.
- docker rm [container_id]: Remove a container.
- docker rmi [image_id]: Remove an image.
- docker exec -it [container_id] /bin/bash: Access a running container.

## Networks and Volumes

- docker network ls: List all networks.
- docker network create [network_name]: Create a new network.
- docker network inspect [network_name]: Display detailed information about a network.
- docker network rm [network_name]: Remove a network.
- docker volume ls: List all volumes.
- docker volume create [volume_name]: Create a new volume.
- docker volume inspect [volume_name]: Display detailed information about a volume.
- docker volume rm [volume_name]: Remove a volume.

## Inspecting and Logging

- docker inspect [container_id]: Inspect a container or image.
- docker logs [container_id]: Fetch the logs of a container.
- docker logs -f [container_id]: Follow the logs of a container in real-time.
- docker stats: Display a live stream of container(s) resource usage statistics.
- docker history [image]: Show the history of an image.
