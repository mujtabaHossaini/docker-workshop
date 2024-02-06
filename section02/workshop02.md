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





