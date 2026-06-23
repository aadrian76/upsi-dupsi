<div style="text-align: justify;">
<details open>
  <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
    Table of Contents
  </summary>

  [[_TOC_]]
</details>


## 📝 Changelog

<br>

| Author | Modification Date | Changes               |
|--------|-------------------|-----------------------|
|        | 25/02/2025        | First Version Created |

<br>

---


# What is a Container? 🏺

A **container** is like a magical travel case for your application. It packs up all the needed libraries, configs, and dependencies so the app can run anywhere (think “shipping your code to a foreign galaxy but it still works seamlessly”). It's less hefty than a full virtual machine because containers share the OS kernel instead of booting a new OS each time.

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://www.docker.com/app/uploads/2021/11/container-what-is-container.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Container on a host, living its best life</div>
</div>

  

### Container vs. Virtual Machine 🎩 vs 🏠

- **VM**: Creates an entire OS for each instance. Feels like moving your entire house each time you want to travel.

- **Container**: Just brings what you need (your clothes and a toothbrush) and uses the host OS. Lighter, faster. Perfect for the minimalistic lifestyle.

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://www.docker.com/app/uploads/2021/11/docker-containerized-and-vm-transparent-bg.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="container vs VM">
    <div style="color: gray; font-size: small; font-style: italic;">Container vs. VM – who will reign supreme?</div>
</div>


---

## Docker Architecture 🏗️

**Docker** uses a client-server approach:

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://www.cherryservers.com/v3/assets/blog/2022-12-20/02.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="Docker Architecture">
    <div style="color: gray; font-size: small; font-style: italic;">One big happy Docker family</div>
</div>

- **Docker Client**: You run commands like `docker build` or `docker run`. The client then pesters the Docker daemon.

- **Docker Daemon**: The actual muscle behind Docker. It listens to requests and does the real work—managing images, containers, networks, etc.

- **Docker Registry**: Think “Docker Hub” or your private registry, storing images so you can share them.

- **Docker Objects**: Images, containers, networks, volumes—like Lego bricks you piece together.

---

## Docker Objects 🧩

### Images

A **Docker image** is your blueprint: each layer adds something (like FROM ubuntu, RUN apt-get install, etc.). They’re read-only, so to get something living and breathing, you run a container from that image.

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://k21academy.com/wp-content/uploads/2021/04/0_CP98BIIBgMG2K3u5.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="Container compilation process">
    <div style="color: gray; font-size: small; font-style: italic;">Container build layers in action</div>
</div>

**Dockerfile**: A list of instructions for building an image—like a cooking recipe, but for containers. Every command is a layer.

### Containers 🍱

When you “run” an image, you get a container. It’s ephemeral by default—once the container is gone, any changes not saved externally vanish into the void.

```bash

docker pull

# -d background
docker run -d --name myubuntu ubuntu

# Remove container to allow to reuse name
docker rm myubuntu

# -i interactive. Will prevent container from exiting if there is no process attached
docker run -d --name myubuntu -i ubuntu

# Run command inside container
docker exec myubuntu whoami

# Spawn shell. -it allocates pseudo-TTY terminal and keeps it open for interactive communication
docker exec -it myubuntu bash

# List (running) containers
docker ps

# List (all) containers
docker ps -a

# Display running processes inside container
docker top myubuntu

docker run -d --name webserver --env APP=nginx nginx:1.21.3

```
**System commands**

```bash
docker system events

# Image layers and dockerfile instructions
docker history imageid

# Get running processes inside container
docker top containerid

# Get container resource limits
docker stats
```
**Pro Tip**: If you want to keep data, either commit a new image or map volumes. Otherwise, say goodbye to your data when the container is removed.

### Data in docker 🏗️

Docker has two options for containers to **store files** on the host machine: *volumes* and **bind mounts**. Docker also supports tmpfs mount, which stores files in memory on the host machine, but such files are not persistent.


The data looks the same from within the container. It is exposed as a directory or a single file in the container's filesystem.

- **Volumes:** Are stored in a part of the host filesystem which is managed by docker (/var/lib/docker/volumes/). Non-docker processes should not modify this part of the filesystem. **Best way to persist data in docker.**

- **Bind mounts:** Stored anywhere on the host system, even on important system files or directories. Non-docker processes on the host can modify them at any time.

- **tmpfs:** Stored in host memory and never written to the host system's filesystem.

```bash

# Volumes (Production)

docker volume create demo

docker volume create demo2

docker volume remove demo2

docker volume ls

docker run --name ubuntu -d -v demo:/opt -it ubuntu:20.04

# Bind mounts (Development)

docker run --name ubuntu2 -d -v /opt:/opt -it ubuntu:20.04

docker run --name volumemount -v data:/src ubuntu:20.04 "/bin/bash" "-c" "echo test>>/src/hello.txt"

# Remove unused and temporary disk space, networks, volumes

docker system prune

# Show disk space used by docker

docker system df

```

# Docker Networking 🌐

Containers usually live in their own bubble. Publish ports with `-p` to expose them, or connect containers to the same network to let them talk to each other. Common network drivers:

- **bridge**: Default, containers on the same bridge can talk to each other, external access if you publish a port.

- **host**: Container uses the host’s network interface. More speed, less isolation.

- **macvlan**: Container gets its own MAC & IP on the local LAN. Some advanced networking wizardry.

- **none**: No network for you—like a hermit container.

```bash
docker network ls

docker network create mybridge

docker run --network mybridge ...

docker network connect mybridge myubuntu```
````

By default, containers lose data once they’re gone (like ephemeral goldfish memory). If you want persistence:

*   **Volumes**: Docker-managed directories in `/var/lib/docker/volumes/`. Best for production.

*   **Bind mounts**: Map a host directory directly. Great for dev, but be careful you don’t override system directories.

*   **tmpfs**: Lives in host memory, not persistent.

```docker volume create myvolume docker run -d -v myvolume:/app --name ubuntu ubuntu```

```docker system prune   # clean up unused stuff docker system df      # show disk usage```

---

Building an Image Using Dockerfile 🏗️

A **Dockerfile** defines steps to create an image. Then you build it with `docker build`.


`docker build -t myimage:latest . docker run -d --name myapp myimage:latest`

**Sample Dockerfile**:

```dockerfile

# FROM specify the underlying operating system you will use to build the image

FROM python:3-alpine3.15

# WORKDIR set the default working directory

WORKDIR /app

# COPY startup script

COPY . .

# RUN any required dependencies by running the necessary commands

RUN apk add --no-cache gawk sed bash grep bc coreutils \

    && pip install -r requirements.txt \

    && chmod +x run.sh

# EXPOSE port 8000 for communication to/from server

EXPOSE 8000

# CMD specifies the command to be executed when the container starts

CMD ["/app/run.sh"]

```

*   **FROM**: Base image

*   **WORKDIR**: Default working directory

*   **COPY**: Bring local files into image

*   **RUN**: Install packages, build dependencies

*   **EXPOSE**: Inform (but not enforce) which port the container listens on

*   **CMD**: The default command when container starts

**Boom**: You have your own container image. Enjoy your microservices meal! 🍴

</div>