---
tags:
  - ✅
sr-due: 2026-07-09
sr-interval: 702
sr-ease: 270
---
⬅️ [[FEM Docker]]
- Docker is a command line tool that makes creating, updating packaging, distributing, and running containers significantly easier
-  it creates a new environment that's isolated by namespace and limited by cgroups and chroot'ing you into it

🤔 **What is Docker Hub?**
Docker Hub is a public registry of pre-made containers (it's like npm for containers)
`docker pull mongo:3` - will pull the mongo image

🤔 **What are images?**
- a blueprint that contains the instructions to build a container. It's an immutable snapshot of the file system and configuration of an application. Images can be easily shared between developers.

```shell
docker images # list all images
```

You can use images to build other images and build on the work of others

```bash
# docker command for running skinny linux (alpine)
# starts you in an Alpine ash shell inside of a container 
# as the root user of that container

# run means we'll be executing docker (as opposed to building it)

# By default containers run and then exit as soon as they're done
# that's why we add the -it flag

docker run -it alpine:3.10
```

🤔 **And what are containers?**
- A container is a executable package that contains everything needed to run an application. It will always run the same, regardless of infrastructure, in a sandboxed environment. It is a running instance of an image.
 ```shell
docker ps -a # list all containers
```

**So, first you build an image, then you run a container.**

🤔 **How do you print out currently running containers?**
```bash
docker ps
```

🤔 **And how do you kill it?**
```bash
docker kill <id or name>

# and to kill all running containers
docker kill $(docker ps -q)
```

You can name your container:
```bash
docker run -dit --name my-ubuntu ubuntu:bionic
docker kill my-ubuntu
```

🤔 **How to free up unused docker space?**
```bash
 docker container prune
 ```
 
 🤔 **How do you automatically cleanup the container?**
 ```bash
docker run --rm -dit --name my-ubuntu ubuntu:bionic
docker kill my-ubuntu
```

🤔 **How to run a container that comes with node?**
```bash
# Stretch refers to the version of Debian 
# (which is what the Node.js uses by default.)

docker run -it node:12-stretch
```

🤔 **Run it and get dropped in bash?**
```bash

# anything we put after get's evaluated instead of 
# the default command identified by the container
# in node's case that would be node

docker run -it node:12-stretch bash
```

🤔 **What is the difference between `docker run` and `docker exec`?**

- `docker run` will start a new container  
- `docker exec` runs the command in an already-running container