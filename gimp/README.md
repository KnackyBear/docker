![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/jnvinet/gimp?logo=docker) ![Docker Automated build](https://img.shields.io/docker/automated/jnvinet/gimp?logo=docker) ![Docker Pulls](https://img.shields.io/docker/pulls/jnvinet/gimp?logo=docker) ![GitHub last commit](https://img.shields.io/github/last-commit/julienvinet/dockerfiles?logo=github) 

# Running command

```
docker run -d \
    --net host \
    -v /etc/localtime:/etc/localtime:ro \
    -v /etc/passwd:/etc/passwd:ro \
    -v "${HOME}:${HOME}" \
    -e "DISPLAY=unix${DISPLAY}" \
    -u $(id -u):$(id -g) \
    --name gimp \
    jnvinet/gimp "$@"
```