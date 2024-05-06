# Activity 9

#### Install docker on EC2 and explore the docker commands (docker images, containers, volumes, network)

<mark>Please Reload couple of times, At times, screenshots may not load all times as more number od screen shots are attached</mark>

## Docker Image commands

### 1. To Check the Docker Version

#### Command

```bash
docker --version
```

#### Screenshot

![alt text](/images/Activity9/docker_version.png)

### 2. To pull the image

#### Command

```bash
docker pull hello-world
```

#### Screenshot

![alt text](/images/Activity9/pull_image.png)

### 3. To list all images

#### Command

```bash
docker images
```

#### Screenshot

![alt text](/images/Activity9/list_images.png)

### 4. To get the histry of the image

#### Command

```bash
# Using Image name
docker history hello-world

# Using Image Id
docker history d2c94e258dcb
```

#### Screenshot

**Using Image name**

![alt text](/images/Activity9/history_img_name_.png)

**Using Image ID**

![alt text](/images/Activity9/history_img_id.png)

### 5. To inspect an image

#### Command

```bash
# Using Image name
docker inspect hello-world

# Using Image Id
docker inspect d2c94e258dcb
```

#### Screenshot

**Using Image name**

![alt text](/images/Activity9/inspect_img_name.png)

**Using Image ID**
![alt text](/images/Activity9/inspect_img_id.png)

### 6. To tag target_image that refers to source_image

#### Syntax

```bash
docker tag <local_img_name>:<local_img_tag> <source_img_name>:<source_img_name>
```

#### Example

```bash
# To tag the image
docker tag ubuntu:latest myubuntu:1.0

# To list the Images
docker images
```

#### Screenshot

**Initial Image**

![alt text](/images/Activity9/docker-images-list.png)

**Tagging ubuntu Image**

![alt text](/images/Activity9/tag-ubuntu-img.png)

**Listing images**

![alt text](/images/Activity9/tag-list-img.png)

### 7. To remove an image

#### Syntax

```bash
docker rmi <image_name>
```

#### Command

```bash
docker rmi hello-world
```

#### Screenshot

![alt text](/images/Activity9/img-remove.png)

### 8. To remove unused images

#### Command

```bash
docker image prune
```

#### Screenshot

![alt text](/images/Activity9/docker-images-list.png)

### 9. To build an Image

#### Syntax

```bash
Docker build -t <image_name>:<tag_name> <path>
```

#### Command

```bash
Docker build -t ubuntu:latest .
```

#### Screenshot

![alt text](/images/Activity9/img-build.png)

### 10. To load an image

#### Command

```bash
docker load < busybox.tar.gz
```

#### Screenshot

![alt text](/images/Activity9/img-load.png)

### 11. To save an Image

#### Command

```bash
docker save busybox > busybox.tar
```

#### Screenshot

![alt text](/images/Activity9/img-save.png)

### 12. To push the image

#### Command

```bash
# To Login in to Docker
docker login

# To tag an image
docker tag ubuntu:latest visshnnu/test:4.0

# To push the image
docker push visshnnu/test:3.0
```

#### Screenshots

From Terminal:

![alt text](/images/Activity9/img-push.png)

From Docker account:

![alt text](/images/Activity9/img-repo.png)

## Docker Container Commands

### 1. To list running containers

#### Command

```bash
docker ps
```

#### Screenshot

![alt text](/images/Activity9/cont-ps.png)

### 2. To list running and not running containers

#### Command

```bash
docker ps -a
```

#### Screenshot

![alt text](/images/Activity9/cont-ps-a.png)

### 3. To start a container

#### Command

```bash
# Start container using container id
docker start e8001273d832

# Start container using container name
docker start suspicious_northcutt
```

#### Screenshot

![alt text](/images/Activity9/cont-start.png)

### 4. To stop a container

#### Command

```bash
# Stop container using container id
docker stop e8001273d832

# Stop container using container name
docker stop suspicious_northcutt
```

#### Screenshot

![alt text](/images/Activity9/cont-stop.png)

### 5. To pause a container

#### Command

```bash
# Pause container using container id
docker pause e8001273d832

# Pause container using container name
docker pause suspicious_northcutt
```

#### Screenshot

![alt text](/images/Activity9/cont-pause.png)

### 6. To unpause a container

#### Command

```bash
# Unpause container using container id
docker unpause e8001273d832

# Unpause container using container name
docker unpause suspicious_northcutt
```

#### Screenshot

![alt text](/images/Activity9/cont-unpause.png)

### 7. To kill a conatainer

#### Command

```bash
# kill container using container id
docker kill e8001273d832

# kill container using container name
docker kill suspicious_northcutt
```

#### Screenshot

![alt text](/images/Activity9/cont-kill.png)

### 8. To attach a container

#### Command

```bash
# Attach container using container id
docker attach e8001273d832

# Attach container using container name
docker attach suspicious_northcutt
```

#### Screenshot

![alt text](/images/Activity9/cont-attach.png)

### 9. To see logs of a conatiner

#### Command

```bash
# Logs container using container id
docker logs e8001273d832

# Logs container using container name
docker logs suspicious_northcutt
```

#### Screenshot

![alt text](/images/Activity9/cont-logs.png)

### 10. To run a container

#### Command

```bash
# To Check the hostname
hostname

# To run the docker container
docker run -it myubuntu:1.0 /bin/bash

# To check the hostname
hostname
```

#### Screenshot

![alt text](/images/Activity9/cont-run.png)

### 11. To remove a Container

#### Command

```bash
docker rm 38d3ea0084bc
```

#### Screenshot

![alt text](/images/Activity9/cont-rm.png)

### 12. To Inspect a Container

#### Command

```bash
docker inspect eaee768f83d7
```

#### Screenshot

![alt text](/images/Activity9/cont-inspect.png)

### 13. To check the load of the container

#### Command

```bash
docker top eaee768f83d7
```

#### Screenshot

![alt text](/images/Activity9/cont-top.png)

## Docker Volume Commands

### 1. To create a Volume

#### Syntax

```bash
docker volume create <volume_name>
```

#### Command

```bash
docker volume create hello
```

#### Screenshot

![alt text](/images/Activity9/vol-create.png)

### 2. To list volumes

#### Command

```bash
docker volume ls
```

#### Screenshot

![alt text](/images/Activity9/vol-ls.png)

### 3. To Inspect a Volume

#### Syntax

```bash
docker inspect <volume_name>
```

#### Command

```bash
docker inspect hello
```

#### Screenshot

![alt text](/images/Activity9/vol-inspect.png)

### 4. To remove a specific volume

#### Syntax

```bash
docker volume rm <volume_name>
```

#### Command

```bash
docker volume rm hello
```

#### Screenshot

![alt text](/images/Activity9/vol-rm.png)

### 5. To remove unused volumes

#### Command

```bash
docker volume prune
```

#### Screenshot

![alt text](/images/Activity9/vol-prune.png)

## Docker Network Commands

### 1. To list networds

#### Command

```bash
docker network ls
```

#### Screenshot

![alt text](/images/Activity9/net-ls.png)

### 2. To create a network to a bridge driver

#### Command

```bash
docker network create my_network
```

#### Screenshot

![alt text](/images/Activity9/net-create.png)

### 3. To inspect a network

#### Command

```bash
# Using network ID
docker network inspect af589d31f9ab
```

#### Screenshot

![alt text](/images/Activity9/net-inspect.png)

### 4. To attach a new container to the new network

#### Command

```bash
docker run -it --name=host --network=my_network myubuntu:1.0 /bin/bash
```

#### Screenshot

![alt text](/images/Activity9/net-connect.png)

### 5. To disconnect the network and container

#### Command

```bash
docker network disconnect multi-host-network container1
```

### 6. To remove unused networks

#### Command

```bash
docker network prune
```

#### Screenshot

![alt text](/images/Activity9/net-prune.png)

### 7. To remove a specific network

#### Command

```bash
docker network rm my_network
```

#### Screenshot

![alt text](/images/Activity9/net-remove.png)
