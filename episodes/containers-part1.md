---
title: "Basics of Containers with Docker"
teaching: 10
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is a Docker image?
- What is a Docker container?
- How do you start and stop a container?
- How do retrieve output from a container to a local machine?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Explain the difference between a Docker image and a Docker container
- Retrieve a Docker image from the cloud
- Start a Docker container running on a local machine
- Use the command line to check the status of the container
- Clean the environment by stopping the container

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

**TODO** Flavor text introducing containers. Why we use them. Include at least 
a couple use cases. If necessary, provide high level distinction from Virtual 
Machines. 

### Images versus containers

**TODO** Flavor text introducing images vs. containers

#### Images are

1. Read-only
2. Contain instructions (in a file called a "Dockerfile" - we talk about 
Dockerfiles later in the lesson)
3. They do not actually "do" anything

#### Containers are

1. Modifiable (while running)
2. Can include files and programs (like your computer!)
3. Can run analyses or web applications (and more)

**TODO**: Analogy for images vs. containers

Images are blueprints, containers are buildings

images are for Platonists, containers for nominalists.


:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::: instructor

**TODO**: Anything the instructor should be aware of. Maybe here's a point for 
an image of some sorts.

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge 

## Challenge 1: Images versus containers

You instructor introduced one analogy for explaining the difference between a 
Docker image and a Docker container. What is another way to explain images and 
containers?

:::::::::::::::::::::::: solution 

Several analogies exist, and here are a few:

- An image is a recipe, say, for your favorite curry, while the container is 
the actual curry dish you can eat.
- "Think of a container as a shipping container for software - it holds 
important content like files and programs so that an application can be 
delivered efficiently from producer to consumer. An image is more like a 
read-only manifest or schematic of what will be inside the container."
(from [Jacob Schmitt](https://circleci.com/blog/docker-image-vs-container/))
- If you are familiar with object-oriented programming, you can think of an 
image as a class, and a container an object of that class. 

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

### Working with containers

One thing to note right away is that a lot of the work of running containers 
happens through the command line interface. That is, we do not have a graphical 
user interface (GUI) with menus to work with. Instead, we type commands into a 
terminal for starting and stopping containers. 

**TODO** General overview of what we do (copy them, start them, stop them)

#### Retrieving images

**TODO** docker pull 

#### Starting an image

**TODO** docker start

#### Status check

**TODO** docker ps

#### Using the container

**TODO** Do something in OpenRefine

#### Stopping the container

**TODO** docker stop (after docker ps)

::::::::::::::::::::::::::::::::::::: challenge 

## Challenge 2: Checking the status of containers

We saw before that we could check the status of running containers by using the 
command `docker ps`. What happens when you run the same command now? What about
when you run the same command with the `-a` flag?

:::::::::::::::::::::::: solution 

- `docker ps` will show the status of all running containers. If you have no 
containers running, and you probably do not at this point of the lesson, you 
should see an empty table, like:
```
$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
$ 
```
- `docker ps -a` will show all containers that are running or _have been_ run 
on the machine. This includes the container that we stopped earlier.
```
$ docker ps -a
CONTAINER ID   IMAGE                      COMMAND                  CREATED         STATUS                       PORTS     NAMES
906072ff88f6   felixlohmeier/openrefine   "/app/refine -i 0.0.…"   2 days ago      Exited (143) 2 days ago                determined_torvalds

$
```
Note the date information (in the `CREATED` and `STATUS` fields) and the 
container name (the `NAMES` field) will likely be different on your machine.

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge 

## Challenge 3: Order of operations

Rearrange the following commands to (in the following order) (1) start the 
OpenRefine container, (2) find the container image ID of the running OpenRefine 
container, and (3) terminal the OpenRefine container.

```
docker stop <container ID>
docker run -p 3333:3333 felixlohmeier/openrefine
docker ps
```

:::::::::::::::::::::::: solution 

```
docker run -p 3333:3333 felixlohmeier/openrefine
docker ps
docker stop <container ID>
```

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::



::::::::::::::::::::::::::::::::::::: callout

**TODO** Add any notes that may be relevant, but not necessary for lesson?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints 

- Containers are a way to provide a consistent environment for reproducible 
work.
- Use `docker pull` to copy an image to your machine
- Use `docker start` to start running a container
- Use `docker ps` to check the status of running containers
- Use `docker stop` to stop running a container

::::::::::::::::::::::::::::::::::::::::::::::::
