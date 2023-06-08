+ Docker is a set of PaaS (platform as a service) product that use OS-level virtualization to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries, and configuration files; they can communicate with each other through well-defined channels.

## **Dockerfile**

+ Docker can build images automatically by reading the instructions from a Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using docker build users can create an automated build that executes several command-line instructions in succession.

## **Images**

+ An image is responsible for setting up the application and environment that will exist inside the container. The important thing to understand is that images are read-only. You do not make edits to an image; you make edits to the Dockerfile and then build a new image.

## **Container**

+ The container is what actually runs our app. Think of the container like an isolated Linux box. It’s essentially a lighter weight virtual machine. The point of having a container is standardization. An application only has to care about the container it’s run in.
+ No more, “But it works on my machine!” If an app runs in a container, it will work the same way no matter where the container itself is hosted. This makes both local development and production deployments much, much easier.

## **Docker Commands**

```docker
docker build -t image-name:tag .
docker run -p 5000:8080 <image-id>
```

### Purging All Unused or Dangling Images, Containers, Volumes, and Networks
+ Docker provides a single command that will clean up any resources — images, containers, volumes, and networks — that are _dangling_ (not tagged or associated with a container):

```docker
docker system prune
```
+ To additionally remove any stopped containers and all unused images (not just dangling images), add the `-a` flag to the command:

```docker
docker system prune -a
```

## Removing Docker Images

### Remove one or more specific images

+ Use the `docker images` command with the `-a` flag to locate the ID of the images you want to remove. This will show you every image, including intermediate image layers. When you’ve located the images you want to delete, you can pass their ID or tag to `docker rmi`:

**List:**

```docker
docker images -a
```

**Remove:**

```docker
docker rmi Image Image
```

### Remove dangling images

+ Docker images consist of multiple layers. Dangling images are layers that have no relationship to any tagged images. They no longer serve a purpose and consume disk space. They can be located by adding the filter flag `-f` with a value of `dangling=true` to the `docker images` command. When you’re sure you want to delete them, you can use the `docker image prune` command:

**Note:** If you build an image without tagging it, the image will appear on the list of dangling images because it has no association with a tagged image. You can avoid this situation by [providing a tag](https://docs.docker.com/engine/reference/commandline/build/#/tag-image--t) when you build, and you can retroactively tag an image with the [`docker tag`](https://docs.docker.com/engine/reference/commandline/tag/) command.

**List:**

```docker
docker images -f dangling=true
```

**Remove:**

```docker
docker image prune
```

### Removing images according to a pattern

+ You can find all the images that match a pattern using a combination of `docker images` and [`grep`](https://www.digitalocean.com/community/tutorials/using-grep-regular-expressions-to-search-for-text-patterns-in-linux). Once you’re satisfied, you can delete them by using [`awk`](https://www.digitalocean.com/community/tutorials/how-to-use-the-awk-language-to-manipulate-text-in-linux) to pass the IDs to `docker rmi`. Note that these utilities are not supplied by Docker and are not necessarily available on all systems:

**List:**

```docker
docker images -a |  grep "pattern"
```

**Remove:**

```docker
docker images -a | grep "pattern" | awk '{print $3}' | xargs docker rmi
```

### Remove all images

+ All the Docker images on a system can be listed by adding `-a` to the `docker images` command. Once you’re sure you want to delete them all, you can add the `-q` flag to pass the image ID to `docker rmi`:

**List:**

```docker
docker images -a
```

**Remove:**

```docker
docker rmi $(docker images -a -q)
```

## Removing Containers

### Remove one or more specific containers

+ Use the `docker ps` command with the `-a` flag to locate the name or ID of the containers you want to remove:

**List:**

```docker
docker ps -a
```

**Remove:**

```docker
docker rm ID_or_Name ID_or_Name
```

### Remove a container upon exiting

+ If you know when you’re creating a container that you won’t want to keep it around once you’re done, you can run `docker run --rm` to automatically delete it when it exits:

**Run and Remove:**

```docker
docker run --rm image_name
```

### Remove all exited containers

+ You can locate containers using `docker ps -a` and filter them by their status: `created`, `restarting`, `running`, `paused`, or `exited`. To review the list of `exited` containers, use the `-f` flag to filter based on status. When you’ve verified you want to remove those containers, use `-q` to pass the IDs to the `docker rm` command:

**List:**

```docker
docker ps -a -f status=exited
```

**Remove:**

```docker
docker rm $(docker ps -a -f status=exited -q)
```

### Remove containers using more than one filter

+ Docker filters can be combined by repeating the filter flag with an additional value. This results in a list of containers that meet either condition. For example, if you want to delete all containers marked as either `created` (a state which can result when you run a container with an invalid command) or `exited`, you can use two filters:

**List:**

```docker
docker ps -a -f status=exited -f status=created
```

**Remove:**

```docker
docker rm $(docker ps -a -f status=exited -f status=created -q)
```

### Remove containers according to a pattern

+ You can find all the containers that match a pattern using a combination of `docker ps` and `grep`. When you’re satisfied that you have the list you want to delete, you can use `awk` and `xargs` to supply the ID to `docker rm`. Note that these utilities are not supplied by Docker and are not necessarily available on all systems:

**List:**

```docker
docker ps -a |  grep "pattern”
```

**Remove:**

```docker
docker ps -a | grep "pattern" | awk '{print $1}' | xargs docker rm
```

### Stop and remove all containers

+ You can review the containers on your system with `docker ps`. Adding the `-a` flag will show all containers. When you’re sure you want to delete them, you can add the `-q` flag to supply the IDs to the `docker stop` and `docker rm` commands:

**List:**

```docker
docker ps -a
```

**Remove:**

```docker
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```

## Removing Volumes

### Remove one or more specific volumes - Docker 1.9 and later

+ Use the `docker volume ls` command to locate the volume name or names you wish to delete. Then you can remove one or more volumes with the `docker volume rm` command:

**List:**

```docker
docker volume ls
```

**Remove:**

```docker
docker volume rm volume_name volume_name
```

### Remove dangling volumes - Docker 1.9 and later

+ Since the point of volumes is to exist independent from containers, when a container is removed, a volume is not automatically removed at the same time. When a volume exists and is no longer connected to any containers, it’s called a _dangling volume_. 
+ To locate them to confirm you want to remove them, you can use the `docker volume ls` command with a filter to limit the results to dangling volumes. When you’re satisfied with the list, you can remove them all with `docker volume prune`:

**List:**

```docker
docker volume ls -f dangling=true
```

**Remove:**

```docker
docker volume prune
```

### Remove a container and its volume

+ If you created an unnamed volume, it can be deleted at the same time as the container with the `-v` flag. Note that this only works with _unnamed_ volumes. When the container is successfully removed, its ID is displayed. Note that no reference is made to the removal of the volume. If it is unnamed, it is silently removed from the system. If it is named, it silently stays present.

**Remove:**

```docker
docker rm -v container_name
```