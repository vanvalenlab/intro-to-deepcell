# Introduction to Containers and Docker

Containers allow software to run reliably when moved from one computing environment to another. Containers are:

* Isolated from each other

* Bundle their own software, libraries, and configuration files.

* Run by a single OS and thus more lightweight than traditional VMs.

Docker is an industry standard open-source software that builds and runs containers. This tutorial will introduce the `Dockerfile`, building Docker images, and running Docker containers.

## The Dockerfile

A Dockerfile is a script that the `docker` program uses to create a Docker image. A Docker image is a snapshot of an operating system. (Think like someone copied your entire hard drive and saved it as a single file -- that's a Docker image.)

Let's look at a simple example Dockerfile:

```docker
# The base image Docker starts from
FROM python:3.7

# Copy the requirements.txt and install the dependencies
# This pattern prevents the dependencies being re-installed
# Due to an application code change.
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt

# Copy the rest of the package code and its scripts into the WORKDIR
COPY . .

CMD bash
```

The Dockerfile starts with a line declaring the base image. This base image is downloaded and further altered by the remaining steps of the Dockerfile.

```docker
FROM python:3.7
```

Next, we copy over `requirements.txt`, a file that declares and defines all the 3rd party dependencies used in the application, and installs them with pip:

```docker
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
```

Then, we copy over the rest of our application source code.  This is copied over separately from the dependencies to save build time when changing application code but not the dependencies:

```docker
# Copy the rest of the package code and its scripts into the WORKDIR
COPY . .
```

Finally, we define the single process the Docker container will run:

```docker
CMD bash
```

## Building a Docker image

Now that we have a `Dockerfile` we can build the Docker image itself, which will be nothing more than an entire file system, neatly stored as a single file.

From within the `intro-to-deepcell` folder, build the Docker image by executing:

```bash
docker build -t vanvalenlab/intro-to-deepcell:myname .
```

* `docker build` is the command to build a Docker image.

* `-t vanvalenlab/intro-to-deepcell:myname` names the new image `vanvalenlab/intro-to-deepcell:0.1`. Image names should follow the form `$DOCKER_REPOSITORY/$DOCKER_IMAGE:$DOCKER_TAG`.

* The final argument `.` is the build context. Docker uses this context to find a `Dockerfile` to build. Additionally, the `Dockerfile` can be directly specified with `-f Dockerfile.custom`.

To verify your new image is built, check for your docker name and tag in the output of:
```bash
docker images
```

## Running a docker container

A Docker image is an entire operating system, including its entire filesystem, wrapped up in a single file. Now, we're going to breathe life into this file by running it as a container, creating a completely isolated operating system running on your computer.

#### Run an image

```bash
docker run -i -t vanvalenlab/intro-to-deepcell:myname
```

* The `-i` and `-t` flags are important for interacting with the docker container.  Without them, the container will run, but you will not see any output.

You should now be inside the Docker container, a completely isolated software environment running on top of your computer.

#### Port Forwarding

Docker containers are inherently isolated, but applications can be exposed via `port forwarding`. Use the optional run parameter `--port <HOST_PORT>:<CONTAINER_PORT>`.

```bash
# For example, to expose jupyter's default port to traffic
docker run -it -p 8888:8888 vanvalenlab/intro-to-deepcell:myname
```

#### Mounting Volumes

Data from the host machine can be mounted into a docker container using optional run parameter `--volume <DATA_PATH>:<CONTAINER_MOUNT_PATH>`.

```bash
docker run -it -v /host/machine/data:/data vanvalenlab/intro-to-deepcell:myname
```

## Additional Resources

[Here is another useful cheatsheet](https://github.com/wsargent/docker-cheat-sheet) for the many Docker commands and how to use them
