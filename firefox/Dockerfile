FROM debian:sid-slim
LABEL maintainer "Julien Vinet <contact@julienvinet.dev>"

# Init environment
RUN apt-get update && apt-get install -y \
	dirmngr \
	gnupg \
	--no-install-recommends \
	&& apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0AB215679C571D1C8325275B9BDB3D89CE49EC21 \
	&& echo "deb http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu xenial main" >> /etc/apt/sources.list.d/firefox.list \
	&& apt-get update && apt-get install -y \
	ca-certificates \
	ffmpeg \
	firefox \
	hicolor-icon-theme \
	libasound2 \
	libgl1-mesa-dri \
	libgl1-mesa-glx \
	libpulse0 \
	fonts-noto \
	fonts-noto-cjk \
	fonts-noto-color-emoji \
	libcanberra-gtk-module \
	gnome-themes-standard \
	--no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

ENV LANG C.UTF-8

COPY local.conf /etc/fonts/local.conf

RUN echo 'pref("browser.tabs.remote.autostart", false);' >> /etc/firefox/syspref.js

ENTRYPOINT [ "firefox" ]