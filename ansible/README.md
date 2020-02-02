![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/jnvinet/ansible?logo=docker) ![Docker Automated build](https://img.shields.io/docker/automated/jnvinet/ansible?logo=docker) ![Docker Pulls](https://img.shields.io/docker/pulls/jnvinet/ansible?logo=docker) ![GitHub last commit](https://img.shields.io/github/last-commit/julienvinet/dockerfiles?logo=github) 

# Running command

```
docker run --rm \
        -it \
        -v ${PWD}/hosts:/etc/ansible/hosts \
        -v ${PWD}/ansible.cfg:/etc/ansible/ansible.cfg \
        -v ${HOME}/.ssh:/root/.ssh:ro \
        jnvinet/ansible "$@"
```