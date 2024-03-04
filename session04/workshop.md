# Read Only volumes:
```
docker volume create myvol1
```
```
docker volume create myvol2
```
```
docker run -itd --name cent1 -v myvol1:/data1 -v myvol2:/data2:ro centos
```
```
docker exec -it cent1 /bin/bash
```
```
cd /data1
```
```
>file1
```
```
cd /data2; 
```
```
>fil2
```
```
cd /var/lib/docker/volumes/myvol2/_data
```
```
>fil2
```

# Sharing Volumes:

```
docker volume create myvol
```

```
docker run -itd --name cent1 -v myvol:/home centos
```

```
docker run -itd --name cent2 -v myvol:/home centos
```

```
docker exec -it cent1 /bin/bash
```
```
docker exec -it cent2 /bin/bash
```
T1:
```
cd /home
```
```
echo salam > file1
```
T2:
```
cd /home
```
```
cat file1
```
```
echo cent2 >> file1
```
T1:
```
cat file1
```

# Race condition in Volumes:
```
docker volume create
```
```
docker run -itd --name cent1 -v myvol:/home centos
```
```
docker run -itd --name cent2 -v myvol:/home centos
```
```
docker exec -it cent1 /bin/bash
```
```
docker exec -it cent2 /bin/bash
```
```
ping 8.8.8.8 >> /home/ping_out
```
```
ping 4.2.2.4 >> /home/ping_out
```
```
cd /var/lib/docker/volumes/myvol/_data
```
```
tail -f ping_out
```

```

## Docker Networking

# List Docker networks:
```
docker network ls
```

# Creating Docker network:
```
dockeer network create -d bridge localnet
```
creates a network names `localnet` with subnet: 172.17.0.0/16, 172.18.0.0/16 , ....

## Service discovery

# Default bridge network

```
docker run -itd --name cent1
```
```
docker run -itd --name cent2
```
```
docker network inspect bridge
```
```
docker attach cent1
```
```
ping cent2
```
```
ping 172.0.0.3
```







