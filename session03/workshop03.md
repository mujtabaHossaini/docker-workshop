# To limit resources
```
docker run -it --name cent1 -m 400M --memory-swap 1G centos:latest /bin/ash
```

# Dangling images

```
docker tag cetnos:latest mycentos:v1
```

```
docker image prune
```

```
docker rmi mycentos:v1
```
```
docker run -itd --name cent1 centos:latest
```

```
docker rmi -f  centos:latest
```
```
docker images
```
```
docker rmi -f {image_id}
```
```
docker stop cent1
```

```
docker start cent1
```

```
docker pull centos:latest
```

```
docker images
```
```
docker ps
```
```
docker stop1
```
```
docker rm cent1
```
```
docker rm -f cent1
```

# docker commit

```
docker run -itd --name cent1 centos
```
```
>file1
```
```
docker cp file1 cent1:/home
```

```
docker commit cent1 mycentos:v2
```
```
docker images

```
```
docker run -itd --name cent2 mycentos:v2
```

```
docker save -o mycentos.tar.gz mycentos:v2
```

```
docker load < mycentos.tar.gz
```

# To export from a running container:
```
docker export cent1 > mycentos.tar.gz
```

```
docker export --output="mycentos.tar.gz" cent1
```
```
docker import mycentos.tar.gz
```

# Approchaes to persist data outside containers:

1- Volume
2- Bind mount
3- tmpfs

# 1.Creating Docker Volumes:

```
docker volume create myvol
```
```
docker volume ls
```

```
ll /var/lib/docker/volumes/myvol/_data/
```

```
docker run -it --name cent1 -v myvol:/data cetn1
```

```
cd /data/
```

```
>file1
```

```
exit
```

```
docker rm cent1
```

```
docker run -itd --name cent2 -v myvol:/data/ cetnos
```

```
cd /data & ls
```

```
docker inspect --format="{{.Mounts}}" cent1
```

# 2. Persistence using Bind mode

```
docker run -itd --name cent1 --mount type=bind,source=/mnt,target=/mnt cetnos
```

# 3. Tmpfs:

```
docker run -itd --name mycent --tmpfs /tmp centos:latest
```





