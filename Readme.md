# Sample Go Web App

## Building new Container Image Releases

In order to create a new container image release the following steps have to be performed:

1. Build a local container image
2. Tag the container image locally
3. Upload the container image to your container registry


### Building the container image

    docker image build -t smpl-go-web .

### Tagging the image locally

For most docker installations the default registry is docker hub. The resulting image can be viewed online: https://hub.docker.com/repository/docker/fischerjulian/smpl-go-web where `fischerjulian` is to be replaced with your username. If you don't have an account, create one. It's for free.

Then login:

    docker login

Please replace the version 1.0.0 with your new version.

    docker image tag smpl-go-web fischerjulian/smpl-go-web:1.0.0

### Upload the locally tagged image to the default registry

Please replace the version 1.0.0 with your new version.

    docker image push fischerjulian/smpl-go-web:1.0.0

## Run the Container Image Locally

### Run From a Local Image

Assuming you have built the container image locally the container can be run with docker:

    docker container run -p 8080:8080 smpl-go-web

This maps the container port 8080 to your local port 8080 so ensure the port is available.

In order to stop the container obtain its ID by using

    docker container ls

And then

  docker container delete 780037d0b7e3

Where `780037d0b7e3` is to be replaced with the corresponding ID of your container.

### Run From a Pulled Imaged

Instead of building a local version you can also pull a remote image with the specified tag:

    docker image pull fischerjulian/smpl-go-web:1.0.0

A quick look will show which images are locally available.

    docker image ls

These are the images you can use locally. So for the remote image we've downloaded to our
local computer this may look like this:

    docker container run -p 8080:8080 fischerjulian/smpl-go-web:1.0.0
