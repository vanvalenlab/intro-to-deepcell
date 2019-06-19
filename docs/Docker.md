# Docker tutorial

Docker is what you would get if your computer had a baby computer and that baby computer came preconfigured with SSH.

### Step 0: Logging into a lab server

Hey! You wanna login to one of the Van Valen Lab's state-of-the-art, GPU-enabled servers? Well, regardless of how you answered, you should probably do that now. The command to do so is:  
```bash
ssh -X -p 5078 [your_username]@[machine_ip_address]
```

### Step 1:  The Dockerfile

A Dockerfile is a script that the `docker` program uses to create a Docker image. A Docker image is a snapshot of an operating system. (Think like someone copied your entire hard drive and saved it as a single file -- that's a Docker image.)

Let's look at a simple example Dockerfile:

```docker
FROM tensorflow/tensorflow:1.11.0-gpu-py3

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
FROM tensorflow/tensorflow:1.11.0-gpu-py3
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

### Step 2: Building a Docker image

Now that we have a Dockerfile, a script describing a Docker image, we can build the Docker image itself, which will be nothing more than an entire file system, neatly stored as a single file.

From within the `deepcell-tf` folder, build the Docker image by executing:  
```bash
docker build -t [your_username]/deepcell-tf:0.1 .
```

Which is roughly translated as:
```bash
docker build -t $DOCKER_REPOSITORY/$DOCKER_IMAGE:$DOCKER_TAG .
```
Explanations follow.

`docker build` is the command to build a Docker image.

`-t [your_username]/deepcell-tf:0.1` names your Docker image `[your_username]/deepcell-tf` and gives it a version number of `0.1`.

The `.` at the end tells `docker build` where to look for a Docker file. `.` represents the current directory in  all Unix systems (Linux and Macs).

So, you're telling `docker build` to use the Dockerfile in the current directory to build a Docker image, which it should name `[your_username]/deepcell-tf` and assign a version number of `0.1` to.


To verify that everything went according to plan, execute
```bash
docker images
```
to view all Docker images. You should see one with your name and version number.

### Step 3: Launching a Docker container

A Docker image is an entire operating system, including its entire filesystem, wrapped up in a single file. Now, we're going to breathe life into this dull file by running it inside a container, creating a completely isolated operating system running on your computer.

To do this, execute:  
```bash
NV_GPU='[assigned_GPU_number]' nvidia-docker run -i -t -v [volume_location]:[mount_location] [dockerfile_location]
```

You should now be inside the Docker container. This is essentially a completely separate computer inside your computer. Anything that happens in magical Docker land stays in Docker land and doesn't affect your permanent filesystem.

### Additional Resources

[Here is another useful cheatsheet](https://github.com/wsargent/docker-cheat-sheet) for the many Docker commands and how to use them
