# cutter-docker

This repository provides an easy way to deploy the tool cutter in a docker container, as mentioned in the [official cutter repository](https://github.com/radareorg/cutter).

[![Build Status](https://travis-ci.org/ps1337/cutter-docker.png?branch=master)](https://travis-ci.org/ps1337/cutter-docker)

This can be used like
```
touch $PWD/radare2rc && \
mkdir -p $PWD/r2-config && \
mkdir -p $PWD/sharedFolder && \
xhost +local:root && \
sudo docker run \
    -it \
    --name cutter \
    --cap-drop=ALL  \
    --cap-add=SYS_PTRACE \
    -e DISPLAY=$DISPLAY \
    -v /tmp/.X11-unix:/tmp/.X11-unix:ro \
    -v $PWD/sharedFolder:/var/sharedFolder \
    -v $PWD/radare2rc:/home/r2/.radare2rc \
    -v $PWD/r2-config:/home/r2/.config/radare2 \
    ps1337/cutter-docker:latest
```

or by using the `Makefile` (after additional configuration to make it fit your needs) by executing `make build` and `make run`.
