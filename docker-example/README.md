# Example Docker image creation

The example Dockerfile creates a new image from python:3.9 base image and (as
of version 1, 2024-09-12) calls python to print out the installed version.

To build, from this directory (be sure to cd into docker-example) run:

`$ docker build -t jcoliver/python-test .`

To run the container

`$ docker run jcoliver/python-test`

Note that if you add a tag in the build command (e.g. 
`docker build -t jcoliver/python-test:v1` but call `docker run` without 
the version tag, it will try to run the version tagged "latest" and fail:

```
$ docker run jcoliver/python-test
Unable to find image 'jcoliver/python-test:latest' locally
```

## Updating python version

To create a new image, with python 3.12, change the first line to

`FROM python:3.12`

and build and run as above.

## Copy & run local script

To update the Dockerfile so it (1) copies the intro.py script and (2) runs that 
script when the container starts, will need add `COPY` command and update `CMD` 
command, so the Dockerfile looks like:

```
FROM python:3.12
# Copy files in current directory to the container
COPY hello-world.py .
# Run intro.py script on starting container
CMD ["python", "intro.py"]
```

and build and run as above.
