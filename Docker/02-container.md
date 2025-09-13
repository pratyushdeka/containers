What is a container?
- A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another 
- Containers are isolated processes with all of the files it needs to run for each of the application component, runs in its own isolated environment, completely isolated from everything else on the machine

Containers are:
- **Self-contained**. Each container has everything it needs to function with no reliance on any pre-installed dependencies on the host machine
- **Isolated**. Since containers are run in isolation, they have minimal influence on the host and other containers, increasing the security of your applications
- **Independent**. Each container is independently managed. Deleting one container won't affect any others
- **Portable**. Containers can run anywhere! The container that runs on your development machine will work the same way in a data center or anywhere in the cloud!

Run a Docker container
```
$ docker run -d -p 8080:80 docker/welcome-to-docker
```

View your running containers
```
docker ps
```
Output
```
 CONTAINER ID   IMAGE                      COMMAND                  CREATED          STATUS          PORTS                      NAMES
 a1f7a4bb3a27   docker/welcome-to-docker   "/docker-entrypoint...."   11 seconds ago   Up 11 seconds   0.0.0.0:8080->80/tcp       gracious_keldysh
```

Stop your container
- Run `docker ps` to get the ID of the container and the run `docker stop` command as below
```
docker stop <the-contianer-id>
```
