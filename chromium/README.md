![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/jnvinet/chromium?logo=docker) ![Docker Automated build](https://img.shields.io/docker/automated/jnvinet/chromium?logo=docker) ![Docker Pulls](https://img.shields.io/docker/pulls/jnvinet/chromium?logo=docker) ![GitHub last commit](https://img.shields.io/github/last-commit/julienvinet/dockerfiles?logo=github) 

# Running command

```
docker run -d \
        --memory 3gb \
        --net host \
        -v /etc/localtime:/etc/localtime:ro \
        -v /etc/passwd:/etc/passwd:ro \
        -e "DISPLAY=unix${DISPLAY}" \
        -v "${HOME}:${HOME}" \
        -e "PULSE_SERVER=unix:${XDG_RUNTIME_DIR}/pulse/native" \
        -v "${XDG_RUNTIME_DIR}/pulse/native:${XDG_RUNTIME_DIR}/pulse/native" \
        -v /dev/shm:/dev/shm \
        -v /etc/hosts:/etc/hosts \
        --security-opt seccomp:/etc/docker/seccomp/chrome.json \
        --device /dev/snd \
        --device /dev/dri \
        --device /dev/video0 \
        --device /dev/bus/usb \
        --group-add audio \
        --group-add video \
        -u $(id -u):$(id -g) \
        --name chromium \
        jnvinet/chromium
```

# Known issues

Even if WinDevine extensions is installed, Netflix seems to not work properly.
Better to use jnvinet/chrome image if you want to watch Netflix with your browser.