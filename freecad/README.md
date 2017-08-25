## Debian debuild packages
-----
##### Pull image
```
docker pull izone/debuild:freecad
```
### Build Image
```
docker build -t izone/debuild:freecad ./freecad/
```
```
```
##### Run
```
docker run -ti --rm --name Debian \
--net=host \
-e DISPLAY=unix$DISPLAY \
-v /tmp/.X11-unix \
-v $HOME/.Xauthority:/root/.Xauthority \
-v $HOME/debuild_freecad:/root/ \
izone/debuild:freecad bash
```
```
```
##### Building FreeCAD
```
cmake ../FreeCAD \
-DCMAKE_INSTALL_PREFIX:PATH=/usr \
-DOCC_INCLUDE_DIR=/usr/include/opencascade \
-DBUILD_FEM_NETGEN=ON 
```
```
make -j$(nproc)
```

-----
```
-----
### FreeCAD debuild
##### Run
```
docker run --rm --name Debian -h deb \
-v $HOME/debuild_freecad:/root/ \
-ti izone/debuild:freecad bash
```
##### Debuilding
```
debuild -us -uc -j$(nproc) --lintian-opts --profile debian
```
