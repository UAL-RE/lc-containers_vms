# Example Docker image creation

The example Dockerfile creates a new image from python:3.9 base image and (as
of version 1, 2024-09-12) calls python to print out the installed version.

To build, from this directory (docker-example) run:

`$ docker image build -t jcoliver/python-test:v1 .`

To run the container

`$ docker run jcoliver/python-test:v1`

Note without the version tag, it will try to run the version tagged "latest"
and fail:

```
$ docker run jcoliver/python-test
Unable to find image 'jcoliver/python-test:latest' locally
```