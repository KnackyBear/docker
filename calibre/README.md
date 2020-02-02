![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/jnvinet/calibre?logo=docker) ![Docker Automated build](https://img.shields.io/docker/automated/jnvinet/calibre?logo=docker) ![Docker Pulls](https://img.shields.io/docker/pulls/jnvinet/calibre?logo=docker) ![GitHub last commit](https://img.shields.io/github/last-commit/julienvinet/dockerfiles?logo=github) 

# Running command

```
docker run -d \
        --net host \
        -v /etc/localtime:/etc/localtime:ro \
        -v /etc/passwd:/etc/passwd:ro \
        -e "DISPLAY=unix${DISPLAY}" \
        -v "${HOME}:${HOME}" \
        --device /dev/bus/usb \
        -u $(id -u):$(id -g) \
        --name calibre \
        jnvinet/calibre "$@"
```

# Known issues

USB Plug seems to not work properly. For the moment, use mail to send books to your kindle.