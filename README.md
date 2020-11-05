Docker essentials
-----------------

### Download and install docker
https://docs.docker.com/get-docker/

### Docker Hub
https://hub.docker.com/

#### Docker pull

```
docker pull <imagename>
```
e.g. To pull nginx image (https://hub.docker.com/_/nginx)
```
docker pull <nginx>
```

#### Docker run
```
docker run nginx:latest
```
To run in background
```
docker run -d nginx:latest
```
To map the port
```
docker run -d -p 8080:80 nginx:latest
```
To map multiple ports
```
docker run -d -p 8080:80 -p 9000:80 nginx:latest
```
To give a name
```
docker run --name <anyname> -d -p 8080:80 nginx:latest
```

#### docker start
```
docker start <imagename>
```
#### docker stop
``` 
docker stop <imagename>
```
#### docker remove
```
docker rm <imagename>
```
##### force remove
Removes running containers as well
```
docker rm -f <imagename>
```

#### To access the container
```
docker exec -it <name> bash
```
#### Docker ps
To view all the running images
```
docker ps
```
To view all the docker images
```
docker ps -a
```

### Volumes
Mount a volume to share files/folder between host system and container OR between containers
```
docker run --name <anyname> -v <sourcepath>:<destinationpath> -p <websiteport>:<containerport> -d <imagename>:<tag>
```
#### Read only
```
docker run --name <anyname> -v <sourcepath>:<destinationpath>:ro -p <websiteport>:<containerport> -d <imagename>:<tag>
```
#### Share between containers
```
docker run --name <newcontainer> --volumes-from <existingcontainername> -p <websiteport>:<containerport> -d <imagename>:<tag>
```

### DOCKERFILE
https://docs.docker.com/engine/reference/builder/

Add `Dockerfile` in the root folder  
Always build a docker image from a source image

- `FROM` -> is to indicate the source image
- `ADD` -> Add the content to destination folder

Build a docker image from dockerfile
```
docker build --tag <name:tag> <source>

e.g.

docker build --tag website:latest .
```