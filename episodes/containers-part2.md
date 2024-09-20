---
title: "Creating Containers with Docker"
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do you create new Docker images?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Explain how a Dockerfile is used to create Docker images
- Create a Dockerfile to run a command
- Use `docker build` to create a new image
- Update a Dockerfile to run a Python script

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

**TODO** Dockerfiles -> Images -> Containers

**TODO** Might be a good spot for a visual.

**TODO** How do we extend analogies that we presented in episode 1?

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::: instructor

**TODO** Anything instructors should be aware of for this episode?

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

### Dockerfile gross anatomy

**TODO** Cover two commands: `FROM` and `CMD` (or maybe `ENTRYPOINT` instead of 
`CMD`?)

### Creating images from Dockerfiles

**TODO** Explain commands. Note how no new _file_ is created in our directory, 
it gets created...somewhere, though?

`docker build -t ...`

`docker image ls`

### Starting containers

**TODO** This is review.

`docker run ...`

Confirm it ran and quit

`docker ps -a`

::::::::::::::::::::::::::::::::::::: challenge 

## Challenge 1: Update base image

- Update the Dockerfile to have a base image that includes Python version 3.12 
(instead of Python version 3.9)
- Build the image
- Start the container to confirm it is using Python version 3.12

:::::::::::::::::::::::: solution 

### Update the Dockerfile

To change the base image, update the information passed to the `FROM` command. 
That is, open the Dockerfile and change this line:

`FROM python:3.9`

to 

`FROM python:3.12`
 
### Buid the image

In the terminal, use `docker build` to create a new version of the image. 

```bash
docker build -t <username>/python-container
```

This command will over-write the previous version of the image. **TODO** Need 
to test this statement.

### Verify image was updated

In the terminal, use `docker run` to start a container based on the updated 
image.

```bash
docker run <username>/python-container
```
:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

### Copying files into the image

**TODO** Add flavor text about why we might do this.

`COPY ...`

See 
https://stackoverflow.com/questions/32727594/how-to-pass-arguments-to-shell-script-through-docker-run
and
https://www.tutorialspoint.com/how-to-pass-command-line-arguments-to-a-python-docker-container

for example of passing arguments to a script. Passing arguments might be too 
much.

::::::::::::::::::::::::::::::::::::: challenge 

## Challenge 2: Copy a script to run in the container

There is a script (make this a `print("Hello World!")` python script) you want 
to include 

:::::::::::::::::::::::: solution 

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints 

- Dockerfiles include instructions for creating a Docker image
- The `FROM` command in a Dockerfile indicates the base image to build on
- The `CMD` command in a Dockerfile includes commands to execute when a 
container starts running
- The `COPY` command in a Dockerfile copies files from your local machine to 
the Docker image so they are available for use when the container is running

::::::::::::::::::::::::::::::::::::::::::::::::
