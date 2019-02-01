# Docker notes

Docker runs containers, which are created from images. Docker containers can communicate with each other.

## Containers

Run apache in docker (8081 is locally accessible port)
```
docker container run -d -p 8081:80 --name myapache httpd
```
See containers -a for all, even if not running
```
docker container ls -a
```

Delete container
```
docker container rm <container_id>
```

Get bash shell in container
```
docker container exec -it myapache bash
```

SSH into a running docker container:
```
docker run -i <NAME from docker ps> /bin/bash
```

For alpine (busybox)
```
docker run -it --rm name /bin/ash
```

Share folder - changes reflected in container
```
docker run -d -p 80:80 -v $(pwd)/src:/var/www/html -e USERID=$UID cpuinfo
```

View docker container's log files
```
docker logs <container_id>
docker logs --tail 50 --follow --timestamps <container_name>
```


## Dockerfile

Create Dockerfile
```
FROM httpd:2.4
COPY index.html /var/www/html/
```

Create an image called user_test from Dockerfle in current directory
```
docker build -t user_test .
```

Start a container based on user_test, interactively, exposing(publish) port 80 to the host 
```
docker container run -it -p 80:80 user_test
```

Start a container based on user_test, detached
```
docker container run -d -p 80:80 user_test
```

## Images

See images
```
docker image ls
docker images

## Layers

Layers of a Docker image are essentially just files generated from running some command. You can view the contents of each layer on the Docker host at ```/var/lib/docker/aufs/diff```. Layers are neat because they can be re-used by multiple images saving disk space and reducing time to build images while maintaining their integrity.





