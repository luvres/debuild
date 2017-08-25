FROM izone/debuild:jessie
#FROM arm32v7/debian:jessie-slim
#FROM arm64v8/debian:jessie-slim

MAINTAINER Leonardo Loures <luvres@hotmail.com>

ENV FREECAD=/opt/FreeCAD
RUN mkdir -p $FREECAD 

### Packages deps
#-----------------
RUN apt-get update \
    && apt-get install -y \
		doxygen \
		libpyside-dev \
		libqtcore4 \
		libshiboken-dev \
		libxerces-c-dev \
		libxmu-dev \
		libxmu-headers \
		libxmu6 \
		libxmuu-dev \
		libxmuu1 \
		pyside-tools \
		python-dev \
		python-pyside \
		python-matplotlib \
		qt4-dev-tools \
		qt4-qmake \
		libqtwebkit-dev \
		shiboken \
		swig

### Packages build
#------------------
RUN apt-get install -y \
		python-pivy \
		g++ \
		libfreetype6-dev \
		tcl8.5-dev \
		tk8.5-dev \
		automake \
		libhdf5-dev \
	  \
		dictionaries-common \
		wget \
		git \
		gmsh

### cmake 3.0.2
#---------------
RUN apt-get install -y \
    cmake 

### libBoost 1.55
#-----------------
RUN apt-get install -y \
		libboost1.55-dev \
		libboost-filesystem1.55-dev \
		libboost-program-options1.55-dev \
		libboost-python1.55-dev \
		libboost-regex1.55-dev \
		libboost-signals1.55-dev \
		libboost-system1.55-dev \
		libboost-thread1.55-dev

### libMED 3.2.0
#-------------
RUN \
    med_VERSION=3.2.0 && \
    wget -c http://pi/FreeCAD/packages/med_${med_VERSION}-jessie_amd64.deb \
    && dpkg -i med_${med_VERSION}-jessie_amd64.deb \
    && rm med_${med_VERSION}-jessie_amd64.deb

### libCoin 3.1.4
#-----------------
RUN apt-get install -y \
		libcoin80 \
		libcoin80-dev 

### Eigen 3.2.2 - 3.3.0(backports)
#----------------------------------
RUN apt-get install -y \
  	  libeigen3-dev 


### OCCT 7.1.0
#-------------
RUN \
	apt-get install -y \
		libfreeimage3 \
		libtbb2 \
	&& \
    occt_VERSION=7.1.0 && \
    wget -c http://pi/FreeCAD/packages/occt_${occt_VERSION}-jessie_amd64.deb \
    && dpkg -i occt_${occt_VERSION}-jessie_amd64.deb \
    && rm occt_${occt_VERSION}-jessie_amd64.deb

### VTK 7.1.1
#-------------
RUN \
    vtk_VERSION=7.1.1 && \
    wget -c http://pi/FreeCAD/packages/vtk_${vtk_VERSION}-jessie_amd64.deb \
    && dpkg -i vtk_${vtk_VERSION}-jessie_amd64.deb \
    && rm vtk_${vtk_VERSION}-jessie_amd64.deb


### FreeCAD latest Github commit
#--------------------------------
# get FreeCAD
RUN \
    cd \
    && git clone https://github.com/FreeCAD/FreeCAD 


#### Netgen 5.3.1
##----------------
RUN \
    cd \
    && apt-get install -y curl \
		openmpi-bin \
		libopenmpi-dev \
		libtogl-dev \
    && wget https://sourceforge.net/projects/netgen-mesher/files/netgen-mesher/5.3/netgen-5.3.1.tar.gz \
	&& tar zxf netgen-5.3.1.tar.gz \
	&& rm netgen-5.3.1.tar.gz \
    && cd netgen-5.3.1 \
  \
	&& curl -L https://git.launchpad.net/~freecad-maintainers/+git/netgen/plain/debian/patches/nglib-occt7.patch | patch -p1 \
  \
  # building Netgen
    && ./configure \
            --prefix=/usr \
            --enable-occ \
            --with-occ=/usr \
            --with-tcl=/usr/lib/tcl8.5 \
            --with-tk=/usr/lib/tk8.5 \
            --with-togl=/usr/lib/ \
            --enable-shared \
            --enable-nglib \
            --disable-gui \
            --disable-dependency-tracking \
            CXXFLAGS="-DNGLIB_EXPORTS -std=gnu++11" \
  \
    && make -j$(nproc) \
    && make install \
  \
    && cp -fR libsrc /usr/share/netgen 

