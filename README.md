docker-gui-app
==============

Summary of the techniques available to run gui applications inside docker

Choose the technique you want to try :

    ln -sf Dockerfile-<technique> Dockerfile

Then build the container (`firefox` is used as example in all Dockerfiles)

    docker build -t dk-firefox

Shared X11 socket
-----------------

    docker run -d \
        -e DISPLAY=$DISPLAY \
        -v /tmp/.X11-unix:/tmp/.X11-unix \
        dk-firefox


References
----------

- [Running GUI apps with Docker](http://fabiorehm.com/blog/2014/09/11/running-gui-apps-with-docker/)
- [can you run GUI apps in a docker container?](https://stackoverflow.com/questions/16296753/can-you-run-gui-apps-in-a-docker-container)
