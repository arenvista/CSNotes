# Docker

# Table of Contents

## Getting Setup With Docker

Note when we close a container, the data is lost - nothing is saved.

`docker ps` - list all running containers
calling command `docker pull mongo:3` will pull the mongo image with version 3 from the docker hub.

## Docker Images without Docker

We're going to run a docker image by hand using the same techniques we used before (chroot, cgroups, namespaces, etc).
to show they are not magic, just a bunch of zip files.

We can base our images off of other images - in kind of layers.

Essentally, a docker image is just a tarball of a bunch of files which are represented in the entirety as a state of a filesystem.

Let's run some commands 
```bash
# start docker contanier with docker running in it connected to host docker daemon
docker run -ti -v /var/run/docker.sock:/var/run/docker.sock --privileged --rm --name docker-host docker:18.06.1-ce

# run stock alpine container
docker run --rm -dit --name my-alpine alpine:3.10 sh

# export running container's file system
docker export -o dockercontainer.tar my-alpine

# make container-root directory, export contents of container into it
mkdir container-root
tar xf dockercontainer.tar -C container-root/

# make a contained user, mount in name spaces
unshare --mount --uts --ipc --net --pid --fork --user --map-root-user chroot $PWD/container-root ash # this also does chroot for us
mount -t proc none /proc
mount -t sysfs none /sys
mount -t tmpfs none /tmp

# here's where you'd do all the cgroup rules making with the settings you wanted to
```
`docker run -ti -v /var/run/docker.sock:/var/run/docker.sock --privileged --rm --name docker-host docker:18.06.1-ce`
This command creates a container that has a docker client that is connected to the host's docker daemon. This is how we can run docker commands from within a container.
- The command above connects to the docker on the docker on the host machine.

Note `-v /var/run/docker.sock:/var/run/docker.sock` is the flag that allows the container to connect to the host's docker daemon. This is a security risk, so be careful with this.

To build this image recall we are just repeating the steps we did before with chroot, cgroups, namespaces, etc.

```bash
docker run --rm -dit --name my-alpine alpine:3.10 sh
```
This commands run a container in the background.

We can then dump the state of this container into a tarball 

```bash
docker export -o dockercontainer.tar my-alpine

mkdir container-root
tar xf dockercontainer.tar -C container-root/
```
looking into container-root we see the filesystem of the container.

```bash
unshare --mount --uts --ipc --net --pid --fork --user --map-root-user chroot $PWD/container-root ash # Note ash is the shell for alpine
mount -t proc none /proc
mount -t sysfs none /sys
mount -t tmpfs none /tmp
```
This essentally is the same as creating a container. We are just doing it by hand. These are the contents of the docker image.


## Docker Images with Docker

The first thing to learn is how to use docker run.

```bash
docker run --interactive --tty alpine:3.10 # or, to be shorter: docker run -it alpine:3.10
```
This does everything we just did for us.

Note with docker most things are ephemeral. When we close the container, the data is lost. Nothing is saved. 

*** A safe assumption would be if it's not in the docker file you can assume it's going to be lost. ***

Also, note that we can shorten the command as follows:
```bash
docker run -it --tty alpine:3.10 # -it puts us in the container
```
the order is very important. Docker then the docker command, then all the flags, then the name of the container, then whatever command you want to run.

Docker can take up a lot of space this is how we can remove images:
```bash
docker image prune # removes all dangling images
```
We can also run a container in the background with the `-d` flag this stands for detached 
```bash
docker run -it -d ubuntu:bionic 
```
To attach to a running container we can use the `attach` command
```bash
docker attach <container_id>
OR
docker attach <container_name> # if you named the container
```
Recall we can find the container id with `docker ps`

Similarly to kill a process we can use the `kill` command
```bash
docker kill <container_id>
OR
docker kill <container_name> # if you named the container
```

