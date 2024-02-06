Move to the home directory:
```
cd /home
```
Clone the Workshop repository:
```
git clone https://github.com/mujtabaHossaini/docker-workshop.git
```
```
cd /home/docker-workshop/section02
```
Now run the containers using docker compose:
```
docker compose up -d
```

To list  containers:
```
docker container ls
```
```
docker container ps
```

Modify Docker Daemon

```
vim /etc/docker/daemon.json
```
```
{
 "live-restore":false
}
```

Reload Docker service

```
systemctl reload docker
```
Copy files to the container
```
docker cp northwind.sql postgres:/home
```
Conect to the container
```
docker exec -it -u postgres postgres /bin/bash
```
Move to the home directory of the container
```
cd /home
```
Execute the following command inside the container

```
psql -d postgres -U postgres  -f northwind.sql
```
To remove all containers

```
docker rm -f $(docker ps -qa)
```



