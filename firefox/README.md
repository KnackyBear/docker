![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/jnvinet/firefox?logo=docker) ![Docker Automated build](https://img.shields.io/docker/automated/jnvinet/firefox?logo=docker) ![Docker Pulls](https://img.shields.io/docker/pulls/jnvinet/firefox?logo=docker) ![GitHub last commit](https://img.shields.io/github/last-commit/julienvinet/dockerfiles?logo=github) 

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