FROM ubuntu:xenial
MAINTAINER Leonardo Loures <luvres@hotmail.com>

# packages install
RUN \
	apt-get update \
	&& apt-get install -y \
		blhc \
		devscripts \
		dh-make \
		dput-ng \
		how-can-i-help \
		locales \
		mc \
		quilt \
		renameutils \
		spell \
		splitpatch \
		tree \
		curl \
		dh-autoreconf \
  \
	&& apt-get clean \
  \
	&& sed -i '/display-info/s/#//' /etc/lintianrc \
	&& sed -i '/#pedantic/s/#//' /etc/lintianrc \
	&& sed -i '/#display-experimental/s/#//' /etc/lintianrc \
  \
	&& echo "alias grep='grep --color=auto'" >>/etc/bash.bashrc \
	&& echo "alias ls='ls --color=auto'" >>/etc/bash.bashrc \
	&& echo "alias tree='tree -aC'" >>/etc/bash.bashrc \
	&& echo "alias uscan='uscan --verbose --report'" >>/etc/bash.bashrc \
	&& echo "alias apt-cache='LANG=C apt-cache'" >>/etc/bash.bashrc \
	&& echo "alias man='LANG=C man'" >>/etc/bash.bashrc \
	&& echo "export EDITOR=mcedit" >>/etc/bash.bashrc \
	&& echo "export QUILT_PATCHES=debian/patches" >>/etc/bash.bashrc \
	&& echo 'export QUILT_DIFF_ARGS="--no-timestamps --no-index -pab"' >>/etc/bash.bashrc \
	&& echo 'export QUILT_REFRESH_ARGS="--no-timestamps --no-index -pab"' >>/etc/bash.bashrc \
	&& echo "export PS1='XENIAL-\u@\h:\w\$ '" >>/etc/bash.bashrc \
	&& echo "export DEBFULLNAME="Leonardo dos Santos Loures"" >>/etc/bash.bashrc \
	&& echo "export DEBEMAIL="luvres@hotmail.com"" >>/etc/bash.bashrc \
	&& echo "#alias debuildsa='dpkg-buildpackage -sa -k02FEE292' # sua chave GPG" >>/etc/bash.bashrc

WORKDIR /root





