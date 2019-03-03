FROM debian:sid-slim
LABEL maintainer "Julien Vinet <contact@julienvinet.dev>"

# Replace with your own
ARG UID=1000
ARG GID=998

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
	libcanberra-gtk-module \
	fonts-noto \
	fonts-noto-cjk \
	fonts-noto-color-emoji \
	--no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

# Create user for wayland
ENV HOME /home/user
RUN groupadd -g ${GID} wheel && \
	useradd -u ${UID} -g ${GID} -G audio --create-home --home-dir $HOME user && \
 	chown -R user:wheel $HOME

ENV LANG C.UTF-8

COPY local.conf /etc/fonts/local.conf

RUN echo 'pref("browser.tabs.remote.autostart", false);' >> /etc/firefox/syspref.js

WORKDIR $HOME
USER user

ENTRYPOINT [ "firefox" ]