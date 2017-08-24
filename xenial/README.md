## Debian debuild packages
-----
##### Pull image
```
docker pull izone/debuild:xenial
```
```
```
##### Run
```
docker run --rm --name Ubuntu -h deb \
-v $HOME/debuild_xenial:/root/ \
-ti izone/debuild:xenial bash
```
```
```
-----
### Build
```
docker build -t izone/debuild:xenial ./xenial/
```

