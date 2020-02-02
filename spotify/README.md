![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/jnvinet/spotify?logo=docker) ![Docker Automated build](https://img.shields.io/docker/automated/jnvinet/spotify?logo=docker) ![Docker Pulls](https://img.shields.io/docker/pulls/jnvinet/spotify?logo=docker) ![GitHub last commit](https://img.shields.io/github/last-commit/julienvinet/dockerfiles?logo=github) 

# Running command

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
        jnvinet/spotify
```
