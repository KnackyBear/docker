# Running command

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