![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/jnvinet/devbox?logo=docker) ![Docker Automated build](https://img.shields.io/docker/automated/jnvinet/devbox?logo=docker) ![Docker Pulls](https://img.shields.io/docker/pulls/jnvinet/devbox?logo=docker) ![GitHub last commit](https://img.shields.io/github/last-commit/julienvinet/dockerfiles?logo=github) 

# What is this box ?

A developer box with some daily needing tools : npm, node, grunt, python3, pip3, and go.
Please fork this project and add your tools if you need.

# Running command

```
docker run -it --rm \
        --net host \
        -v $PWD:/build
        jnvinet/devbox "$@"
```