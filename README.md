## Debian debuild packages
-----
##### Pull image
```
docker pull izone/debuild:jessie
```
```
```
##### Run
```
docker run --rm --name Debian -h deb \
-v $HOME/debuild_jessie:/root/ \
-ti izone/debuild:jessie bash
```
```
docker run -ti --rm --name Debian \
--net=host \
-e DISPLAY=unix$DISPLAY \
-v /tmp/.X11-unix \
-v $HOME/.Xauthority:/root/.Xauthority \
-v $HOME/debuild_jessie:/root/ \
izone/debuild:jessie bash
```
```
```
-----
### Build
```
docker build -t izone/debuild:jessie .
```
```
```
-----
### FreeCAD debuild
##### Download source
```
apt-get -t jessie-backports source freecad

cd freecad*
```
##### Install depends
```
apt-get -t jessie-backports install \
cmake \
debhelper \
gfortran \
libboost-date-time-dev \
libboost-dev \
libboost-filesystem-dev \
libboost-graph-dev \
libboost-iostreams-dev \
libboost-program-options-dev \
libboost-python-dev \
libboost-regex-dev \
libboost-serialization-dev \
libboost-signals-dev \
libboost-thread-dev \
libcoin80-dev \
libcv-dev \
libeigen3-dev \
libf2c2-dev \
libfltk1.3-dev \
libgts-bin \
libgts-dev \
liboce-foundation-dev \
liboce-modeling-dev \
liboce-ocaf-dev \
liboce-visualization-dev \
libode-dev \
libpyside-dev \
libqt4-dev \
libqtwebkit-dev \
libshiboken-dev \
libsoqt4-dev \
libspnav-dev \
libtool \
libx11-dev \
libxerces-c-dev \
libxext-dev \
libxi-dev \
libxmu-dev \
libxt-dev \
libzipios++-dev \
oce-draw \
python-pyside \
pyside-tools \
python-cxx-dev \
python-dev \
swig \
zlib1g-dev
```
##### Debuilding
```
debuild -us -uc -j$(nproc) --lintian-opts --profile debian
```
