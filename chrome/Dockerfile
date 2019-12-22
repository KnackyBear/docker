# Run Chrome in a container
#
# Thanks to Jess Frazelle for her dockerfile !
# I have just add some stuff to work with wayland
#
# docker run -d \
#	--net host \ # may as well YOLO
#	--cpuset-cpus 0 \ # control the cpu
#	--memory 512mb \ # max memory it can use
#	-v /tmp/.X11-unix:/tmp/.X11-unix \ # mount the X11 socket
#	-e DISPLAY=unix$DISPLAY \
#	-v $HOME/Downloads:/home/chrome/Downloads \
#	-v $HOME/.config/google-chrome/:/data \ # if you want to save state
#	--security-opt seccomp=$HOME/chrome.json \
#	--device /dev/snd \ # so we have sound
#   --device /dev/dri \
#	-v /dev/shm:/dev/shm \
#	--name chrome \
#	jnvinet/chrome
#
# You will want the custom seccomp profile:
# 	wget https://raw.githubusercontent.com/jfrazelle/dotfiles/master/etc/docker/seccomp/chrome.json -O ~/chrome.json

# Base docker image
FROM debian:sid-slim
LABEL maintainer "Julien Vinet <contact@julienvinet.dev>"

# Install Chrome
RUN apt-get update && apt-get install -y \
	apt-transport-https \
	ca-certificates \
	curl \
	gnupg \
	hicolor-icon-theme \
	libcanberra-gtk* \
	libgl1-mesa-dri \
	libgl1-mesa-glx \
	libpango1.0-0 \
	libpulse0 \
    fonts-symbola \
	libv4l-0 \
	--no-install-recommends \
	&& curl -sSL https://dl.google.com/linux/linux_signing_key.pub | apt-key add - \
	&& echo "deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google.list \
	&& apt-get update && apt-get install -y \
	google-chrome-stable \
	--no-install-recommends

COPY local.conf /etc/fonts/local.conf

# Asian fonts
RUN mkdir -p /usr/share/fonts/opentype/adobe-source-han-sans \
	&& wget -q --no-check-certificate https://github.com/adobe-fonts/source-han-sans/releases/download/2.001R/SourceHanSans.ttc -O /usr/share/fonts/opentype/adobe-source-han-sans/SourceHanSans.ttc \
	&& fc-cache -f -v

# Clean
RUN apt-get purge --auto-remove -y curl \
	&& rm -rf /var/lib/apt/lists/*

# Autorun chrome
ENTRYPOINT [ "google-chrome" ]
