# What is Docker?
Docker is an open platform to
- develop
- ship
- run
applications.

Docker enables us to
- separate applications from the infrastructure so that software can be delivered quickly
- can manage infrastructure in the same ways applications are managed
- reduce the delay between writing code and running in production

## [The Docker platform](https://docs.docker.com/get-started/docker-overview/#the-docker-platform)
Docker provides tooling and a platform to manage the lifecycle of containers:
- Develop your application and its supporting components using containers
- The container becomes the unit for distributing and testing your application
- When you're ready, deploy your application into your production environment, as a container or an orchestrated service
	- This works the same whether your production environment is a local data center, a cloud provider, or a hybrid of the two

## [What can I use Docker for?](https://docs.docker.com/get-started/docker-overview/#what-can-i-use-docker-for)
- ### Fast, consistent delivery of your applications
- ### Responsive deployment and scaling
- ### Running more workloads on the same hardware
	- Docker is lightweight and fast
	- Provides viable, cost-effective alternative to hypervisor-based virtual machines, so you can use more of your server capacity to achieve your business goals

## [Docker architecture](https://docs.docker.com/get-started/docker-overview/#docker-architecture)
- Docker uses a client-server architecture
- The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers
- The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon
- The Docker client and daemon communicate using a REST API, over UNIX sockets or a network interface

![[Pasted image 20250913181036.png]]

- Docker daemon
	- The Docker daemon (`dockerd`) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes
	- A daemon can also communicate with other daemons to manage Docker services
- Docker client
	- The Docker client (`docker`) is the primary way that many Docker users interact with Docker
	- When you use commands such as `docker run`, the client sends these commands to `dockerd`, which carries them out
	- The `docker` command uses the Docker API
	- The Docker client can communicate with more than one daemon
- Docker registries
	- A Docker registry stores Docker images
	- Docker Hub is a public registry
- Docker Objects
	- images, containers, networks, volumes, plugins etc. 
	- Images
		-  An image is a read-only template with instructions for creating a Docker container
	- Containers
		- A container is a runnable instance of an image
		- can create, start, stop, move, or delete a container using the Docker API or CLI
		- can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state

##### [Example `docker run` command](https://docs.docker.com/get-started/docker-overview/#example-docker-run-command)
The following command runs an `ubuntu` container, attaches interactively to your local command-line session, and runs `/bin/bash`.
```
$ docker run -i -t ubuntu /bin/bash
```

When you run this command, the following happens (assuming you are using the default registry configuration):

1. If you don't have the `ubuntu` image locally, Docker pulls it from your configured registry, as though you had run `docker pull ubuntu` manually.
2. Docker creates a new container, as though you had run a `docker container create` command manually.
3. Docker allocates a read-write filesystem to the container, as its final layer. This allows a running container to create or modify files and directories in its local filesystem.
4. Docker creates a network interface to connect the container to the default network, since you didn't specify any networking options. This includes assigning an IP address to the container. By default, containers can connect to external networks using the host machine's network connection.
5. Docker starts the container and executes `/bin/bash`. Because the container is running interactively and attached to your terminal (due to the `-i` and `-t` flags), you can provide input using your keyboard while Docker logs the output to your terminal.
6. When you run `exit` to terminate the `/bin/bash` command, the container stops but isn't removed. You can start it again or remove it.