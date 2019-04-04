#
# Spotify container
# From Jessie Frazelle <jess@linux.com> image base
# 
# Adding gnome theme and stuff for wayland.
# Do not need to create a specific user cuz wayland must
# use a user who has xhost permissions.
#
# docker run -d \
#		--net host \
#		-v /etc/localtime:/etc/localtime:ro \
#		-v /etc/passwd:/etc/passwd:ro \
#		-v "${HOME}:${HOME}" \
#		-e "DISPLAY=unix${DISPLAY}" \
#		-e QT_DEVICE_PIXEL_RATIO \
#		-e "PULSE_SERVER=unix:${XDG_RUNTIME_DIR}/pulse/native" \
#   	-v "${XDG_RUNTIME_DIR}/pulse/native:${XDG_RUNTIME_DIR}/pulse/native" \
#		--device /dev/snd \
#		--device /dev/dri \
#		-u $(id -u):$(id -g) \
#		--name spotify \
#		jnvinet/spotify
#

FROM debian:sid-slim
LABEL maintainer "Julien Vinet <contact@julienvinet.dev>"

RUN	apt-get update && apt-get install -y \
	dirmngr \
	gnupg \
	--no-install-recommends \
	&& apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 931FF8E79F0876134EDDBDCCA87FF9DF48BF1C90 \
	&& echo "deb http://repository.spotify.com stable non-free" >> /etc/apt/sources.list.d/spotify.list \
	&& apt-get update && apt-get install -y \
	alsa-utils \
	libgl1-mesa-dri \
	libgl1-mesa-glx \
   	libpulse0 \
	spotify-client \
	xdg-utils \
	libcanberra-gtk-module \
	gnome-themes-standard \
	--no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

ENTRYPOINT	[ "spotify" ]