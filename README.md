# docker
Personnal stuff about docker images

### firefox
Firefox GUI app in a container using Wayland and PulseAudio.

    docker run -d \
		--memory 2gb \
		--net host \
		--cpuset-cpus 0 \
		-v /etc/localtime:/etc/localtime:ro \
		-v /etc/passwd:/etc/passwd:ro \
		-v "${HOME}:${HOME}" \
		-e "DISPLAY=unix${DISPLAY}" \
		-e "PULSE_SERVER=unix:${XDG_RUNTIME_DIR}/pulse/native" \
    	-v "${XDG_RUNTIME_DIR}/pulse/native:${XDG_RUNTIME_DIR}/pulse/native" \
		--device /dev/snd \
		--device /dev/dri \
		-u $(id -u):$(id -g) \
		--name firefox \
		jnvinet/firefox "$@"

### vscode
Visual Studio Code in a container using Wayland.

    docker run -d \
		--net host \
		-v /etc/localtime:/etc/localtime:ro \
		-v /etc/passwd:/etc/passwd:ro \
		-v "${HOME}:${HOME}" \
		-e "DISPLAY=unix${DISPLAY}" \
		-e "PULSE_SERVER=unix:${XDG_RUNTIME_DIR}/pulse/native" \
    	-v "${XDG_RUNTIME_DIR}/pulse/native:${XDG_RUNTIME_DIR}/pulse/native" \
		--device /dev/dri \
		-u $(id -u):$(id -g) \
		-w $(pwd) \
		--name vscode \
		jnvinet/vscode "$@"


### gitlab
A gitlab compose file with NFS related directories.

### lychee
Two compose files:
    - full stack with mariadb and original lychee front from linuxserver.io sources
    - full stack with mariadb and lychee front from linuxserver.io AND lycheesync plugin from my own (forked from GustavePate:master branch)

### lycheesync
Dockerfile to create my own container with lychee front from linuxserver.io and lycheesync plugin (from my github).

### plexmediaserver
A plex mediaserver compose file using container from linuxserver.io and some configurations to use with NFS cluster.

### sonarr
A sonarr compose file using container from linuxserver.io and some configurations to use with NFS cluster.

### spotify
Spotify in a container using Wayland and pulseAudio.

		docker run -d \
		--net host \
		-v /etc/localtime:/etc/localtime:ro \
		-v /etc/passwd:/etc/passwd:ro \
		-v "${HOME}:${HOME}" \
		-e "DISPLAY=unix${DISPLAY}" \
		-e QT_DEVICE_PIXEL_RATIO \
		-e "PULSE_SERVER=unix:${XDG_RUNTIME_DIR}/pulse/native" \
			-v "${XDG_RUNTIME_DIR}/pulse/native:${XDG_RUNTIME_DIR}/pulse/native" \
		--device /dev/snd \
		--device /dev/dri \
		-u $(id -u):$(id -g) \
		--name spotify \
		jnvinet/spotify