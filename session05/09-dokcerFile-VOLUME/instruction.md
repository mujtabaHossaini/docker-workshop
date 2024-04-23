```
docker volume create v1
```

```
cd /var/lib/docker/volumes/myvol/_data
```
```
vim index.html
```
```
salam
```

```
docker run -it --name myapache -v myvol1:/var/www/html -p 80:80 myapache:v1
```


