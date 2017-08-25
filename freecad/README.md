## Debian debuild packages
-----
##### Pull image
```
docker pull izone/debuild:freecad
```
```
```
##### Run
```
docker run --rm --name Debian -h deb \
-v $HOME/debuild_freecad:/root/ \
-ti izone/debuild:freecad bash
```
```
docker run -ti --rm --name Debian \
--net=host \
-e DISPLAY=unix$DISPLAY \
-v /tmp/.X11-unix \
-v $HOME/.Xauthority:/root/.Xauthority \
-v $HOME/debuild_jessie:/root/ \
izone/debuild:freecad bash
```
```
```
-----
### Build
```
docker build -t izone/debuild:freecad ./freecad/
```
```
```
-----
### FreeCAD debuild
##### Download source
```

```
##### Debuilding
```
debuild -us -uc -j$(nproc) --lintian-opts --profile debian
```
