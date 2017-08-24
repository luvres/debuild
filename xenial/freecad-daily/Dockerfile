FROM izone/debuild:xenial
MAINTAINER Leonardo Loures <luvres@hotmail.com>

# ppa FreeCAD Daily
RUN \
	apt-get update && \
	apt-get install -y --no-install-recommends software-properties-common && \
	add-apt-repository -y ppa:freecad-maintainers/freecad-daily && \
	sed -i '/deb-src/s/# //' /etc/apt/sources.list.d/freecad-maintainers-ubuntu-freecad-daily-xenial.list && \
	apt-get update 

# Install Build-Depends:
RUN \
	apt-get install -y \
		cmake \
		debhelper \
		libboost-dev \
		libboost-filesystem-dev \
		libboost-program-options-dev \
		libboost-python-dev \
		libboost-regex-dev \
		libboost-signals-dev \
		libboost-thread-dev \
		libcoin80-dev \
		libeigen3-dev \
		libfreeimage-dev \
		libfreetype6-dev \
		libmedc-dev \
		libopencascade-data-exchange-dev \
		libopencascade-ocaf-dev \
		libopencascade-visualization-dev \
		libproj-dev \
		libpyside-dev \
		libqt4-dev \
		libqt4-opengl-dev \
		libqtwebkit-dev \
		libshiboken-dev \
		libspnav-dev \
		libxerces-c-dev \
		libzipios++-dev \
		lsb-release \
		netgen-headers \
		opencascade-draw \
		pyside-tools \
		python-dev \
		python-ply \
		swig \
		libvtk6-dev





