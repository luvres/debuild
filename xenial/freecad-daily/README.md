## Debian debuild packages
-----
##### Pull image
```
docker pull izone/debuild:xenial-freecad-daily
```
```
```
##### Run
```
docker run --rm --name Ubuntu -h deb \
-v $HOME/debuild_xenial:/root/ \
-ti izone/debuild:xenial-freecad-daily bash
```
```
```
-----
### Build
```
docker build -t izone/debuild:xenial-freecad-daily ./xenial/freecad-daily/
```

-----
### FreeCAD debuild
##### Download source
```
apt-get source freecad-daily

cd freecad-daily*
sed -i '/NETGEN/s/OFF/ON/' debian/rules
```
##### Debuilding
```
debuild -us -uc -j$(nproc) --lintian-opts --profile debian
```

-----
##### Run
```
docker run -ti --rm --name Ubuntu \
--net=host \
-e DISPLAY=unix$DISPLAY \
-v /tmp/.X11-unix \
-v $HOME/.Xauthority:/root/.Xauthority \
-v $HOME/debuild_xenial:/root/ \
izone/debuild:xenial bash
```
```
apt-get install -y wget netgen-headers
```
```
wget -c http://pi/FreeCAD/packages/freecad-daily_0.17~alpha1%2bgit201708222315~ubuntu16.04.1_amd64.deb -O freecad-daily_amd64.deb

wget -c http://pi/FreeCAD/packages/freecad-daily_0.17_NETGEN~alpha1%2bgit201708222315~ubuntu16.04.1_amd64.deb -O freecad-daily_amd64.deb

dpkg -i freecad-daily_amd64.deb
```
```
apt-get -fy install
```



