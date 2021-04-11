# Docker

Docker is a tool designed to make it easier to create, deploy, and run applications by using containers.

## Concepts

* [Context](https://docs.docker.com/engine/context/working-with-contexts/)
* [Network (host ports)](https://docs.docker.com/network/)
* [Storage (volumes)](https://docs.docker.com/storage/volumes/)

## Docker Command Line Interface ([CLI](https://docs.docker.com/engine/reference/commandline/cli/))

* [docker run](https://docs.docker.com/engine/reference/run/)
* [docker image](https://docs.docker.com/engine/reference/commandline/image/)
* [docker volume](https://docs.docker.com/engine/reference/commandline/volume_create/)
* [docker build](https://docs.docker.com/engine/reference/commandline/image_build/)

## Inspect image layers

Images are built using ephemeral layers. We can review the image [history](https://docs.docker.com/engine/reference/commandline/image_history/), to view the commands used to build and image

```bash
docker image history <IMAGE>
```

## Let's make our first image!

We are going to create a simple image

1. Create an empty directory and add a file named "Dockerfile"

```docker
FROM alpine:latest
CMD ["echo", "execute order 66"]
```

2. Build the docker image!

```bash
$ docker image build -t palpatine-image .
```

3. Lets run our image!

```bash
$ docker run palpatine-image
```

## Dockerfile ([reference](https://docs.docker.com/engine/reference/builder/))

Docker can build images automatically by reading the instructions from a Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image.¿

#### FROM
Specifies the image we're extending (if any)

```docker
FROM alpine:latest
```

We can use [Alpine](https://hub.docker.com/_/alpine) for minimalism or [Ubuntu](https://hub.docker.com/_/ubuntu) if we need a more complete distro, as base images

#### CMD

Executes a command, and is only used if no command is given at runtime (with "docker run")

```docker
CMD ["echo", "execute order 66"]
```

> If multiple instances of CMD are present, only the last one is used

#### ENTRYPOINT

Analog to CMD, but **mandatory** (always executed). If used in conjunction with CMD, the ENTRYPOINT is always executed **before**

```docker
ENTRYPOINT ["echo", "i can feel your anger"]
```

> [Difference](https://phoenixnap.com/kb/docker-cmd-vs-entrypoint#:~:text=CMD%20is%20an%20instruction%20that,container%20with%20a%20specific%20executable.) between CMD and ENTRYPOINT

#### RUN

Analog to CMD, but allows the base image to specify command to execute on images, extending the current one

```docker
RUN ["echo", "it will be done, my lord"]
```

#### WORKDIR

Specify the "working directory" for instructions that manage the file system

```docker
WORKDIR /some/different/path
```

#### ADD

```docker
# ["<src>",... "<dest>"]
ADD ["fileFromContext", "/some/dir/"]
```

> Avoid using ADD, use COPY instead !!!

#### COPY

```docker
# ["<src>",... "<dest>"]
COPY ["fileFromContext", "/some/dir/"]
```

> [Difference](https://phoenixnap.com/kb/docker-add-vs-copy) between ADD and COPY

#### EXPOSE

Hints that a port should be "exposed" to the host (NOT "published"). The ports are only published at runtime (with "docker run")

```docker
EXPOSE 8080

# We can also specify a protocol
EXPOSE 6379/TCP
```

> [Difference](https://www.whitesourcesoftware.com/free-developer-tools/blog/docker-expose-port/) between "exposing" and "publishing" ports

#### VOLUME

Specifies a container directory to be mounted as a "volume" at runtime

```docker
VOLUME ["/var/log/"]
```

#### ENV

Set an environment variable

```docker
ENV MY_KEY="my value"
```

#### ARG

Specify "named arguments" for the image. Optionally we can define default values

```docker
ARG <name>[=<default value>]
```

> Arguments can be passed at build time with ```docker build --build-arg <varname>=<value>```

#### ONBUILD

Specify instructions to be executed with an extending image is built (when this image is used as a base for another image)

```docker
ONBUILD <INSTRUCTION>
```

#### USER

Specify the UID and optionally the GID (niche usage)

```docker
USER <user>[:<group>]
```

#### SHELL

Specify the shell to be used by default (niche usage)

```docker
# sh is the default shell
SHELL ["/bin/sh", "-c"]
```



