# Run gimp in a container.
# Thanks to Jess Frazelle for her dockerfile !
#
# docker run -d \
#   --net host \
#	-v /etc/localtime:/etc/localtime:ro \
#   -v /etc/passwd:/etc/passwd:ro \
#	-e DISPLAY=unix$DISPLAY \
#	-v "${HOME}:${HOME}" \
#   -u $(id -u):$(id -g) \
#	--name gimp \
#	jess/gimp
#
FROM debian:bullseye-slim
LABEL maintainer "Julien Vinet <contact@julienvinet.dev>"

RUN apt-get update && apt-get install -y \
	gimp \
    libcanberra-gtk-module \
    gnome-themes-standard \
    libgl1-mesa-dri \
    libgl1-mesa-glx \
	--no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

ENTRYPOINT [ "gimp" ]