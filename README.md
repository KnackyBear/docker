# Dockerfiles
Personnal stuff that I use on my laptop or server

# Running commands

All commands below are made to be use with Wayland and/or PulseAudio.

## Firefox

```
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
```

## Spotify

```
docker run -d \
	--net host \
	-v /etc/localtime:/etc/localtime:ro \
	-v /etc/passwd:/etc/passwd:ro \
	-v "${HOME}:${HOME}" \
	-e "DISPLAY=unix${DISPLAY}" \
	-e "PULSE_SERVER=unix:${XDG_RUNTIME_DIR}/pulse/native" \
	-v "${XDG_RUNTIME_DIR}/pulse/native:${XDG_RUNTIME_DIR}/pulse/native" \
	--device /dev/snd \
	--device /dev/dri \
	-u $(id -u):$(id -g) \
	--name spotify \
	jnvinet/spotify "$@"
```

## VSCode

```
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
```

## VSCodium

```
docker run -d \
	--net host \
	-v /etc/localtime:/etc/localtime:ro \
	-v /etc/passwd:/etc/passwd:ro \
	-v "${HOME}:${HOME}" \
	-e "DISPLAY=unix${DISPLAY}" \
	--device /dev/dri \
	-u $(id -u):$(id -g) \
	-w $(pwd) \
	--name vscodium \
	jnvinet/vscodium "$@"
```