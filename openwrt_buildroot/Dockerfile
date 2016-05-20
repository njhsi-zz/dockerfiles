# /dl - the download repo, /openwrt - the openwrt.git root,
#
#
FROM		debian:stable
LABEL		CMDBUILD="docker build -t njhsi/openwrt_buildroot https://raw.githubusercontent.com/njhsi/dockerfiles/master/openwrt_buildroot/Dockerfile"
LABEL		CMDRUN="docker run njhsi/openwrt_buildroot"

MAINTAINER	njhsi

# gettext for envsubst
RUN		apt-get update && \
			apt-get install -yq git-core build-essential libssl-dev libncurses5-dev unzip gawk && \
			apt-get clean && \
			useradd -m openwrt && \
			echo 'openwrt ALL=NOPASSWD: ALL' > /etc/sudoers.d/openwrt 

#ENTRYPOINT      ["/setup.sh"]
