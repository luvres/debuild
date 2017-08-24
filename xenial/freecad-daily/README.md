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


```
apt-get install \
blt calculix-ccx dbus dbus-x11 fonts-liberation \
fonts-lyx freecad-daily gconf-service gconf-service-backend \
gconf2 gconf2-common graphviz hicolor-icon-theme libatk1.0-0 \
libatk1.0-data libcap-ng0 libcdt5 libcgraph6 libgconf-2-4 \
libgd3 libglade2-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common \
libgvc6 libgvpr2 libjs-jquery-ui libpathplan4 libqtassistantclient4 \
libsoqt4-20 libspooles2.2 libxcursor1 psmisc python-cairo \
python-cycler python-dateutil python-glade2 python-gobject-2 \
python-gtk2 python-imaging python-matplotlib python-matplotlib-data \
python-numpy python-pil python-pivy python-pyparsing python-qt4 \
python-qt4-gl python-sip python-tk python-tz tk8.6-blt2.5 ttf-bitstream-vera
```

