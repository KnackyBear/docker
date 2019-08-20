# VSCodium in a container
FROM debian:buster-slim
LABEL maintainer="Julien Vinet <contact@julienvinet.dev>" app="vscodium"

# Tell debconf to run in non-interactive mode
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y \
	apt-transport-https \
	ca-certificates \
	wget \
	gnupg \
	--no-install-recommends

# Add the vscodium repo
RUN wget -qO - https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/master/pub.gpg | apt-key add -
RUN echo 'deb https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/repos/debs/ vscodium main' | tee --append /etc/apt/sources.list

RUN apt-get update && apt-get -y install \
	codium \
	git \
	libasound2 \
	libatk1.0-0 \
	libcairo2 \
	libcups2 \
	libexpat1 \
	libfontconfig1 \
	libfreetype6 \
	libgtk2.0-0 \
	libpango-1.0-0 \
	libx11-xcb1 \
	libxcomposite1 \
	libxcursor1 \
	libxdamage1 \
	libxext6 \
	libxfixes3 \
	libxi6 \
	libxrandr2 \
	libxrender1 \
	libxss1 \
	libxtst6 \
	libgl1-mesa-dri \
	libgl1-mesa-glx \
	openssh-client \
	libcanberra-gtk-module \
	gnome-themes-standard \
	--no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

ENTRYPOINT [ "/usr/share/codium/codium" ]
