![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/jnvinet/hostess?logo=docker) ![Docker Automated build](https://img.shields.io/docker/automated/jnvinet/hostess?logo=docker) ![Docker Pulls](https://img.shields.io/docker/pulls/jnvinet/hostess?logo=docker) ![GitHub last commit](https://img.shields.io/github/last-commit/julienvinet/dockerfiles?logo=github) 

# Running command

```
docker run --rm -it \
    -v /etc/hosts:/etc/hosts \
    --name hostess \
    jnvinet/hostess "$@"
```

# About Hostess

## What is hostess ?
An idempotent command-line utility for managing your /etc/hosts file.

```
hostess add local.example.com 127.0.0.1
hostess add staging.example.com 10.0.2.16
```

Why? Because you edit /etc/hosts for development, testing, and debugging. Because sometimes DNS doesn't work in production. And because editing /etc/hosts by hand is a pain. Put hostess in your Makefile or deploy scripts and call it a day.

## Original source code
https://github.com/cbednarski/hostess