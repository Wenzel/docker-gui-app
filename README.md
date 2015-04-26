docker-gui-app
==============

Summary of the methods available to run gui applications inside docker

Choose the method you want to try :

    ln -sf Dockerfile-<method> Dockerfile

Then build the container (`firefox` is used as example in all Dockerfiles)

    docker build -t dk-firefox

1 - Shared X11 socket
-----------------

    docker run -d \
        --rm=true \
        -e DISPLAY="$DISPLAY" \
        -v /tmp/.X11-unix:/tmp/.X11-unix:ro \
        dk-firefox



2 - VNC Server
--------------

    docker run -ti \
        --rm=true \
        -e DISPLAY="$DISPLAY" \
        -v /tmp/.X11-unix:/tmp/.X11-unix:ro \
        dk-firefox

Once the container is started, type the following commands to

1. Run an `xvfb` server (X Virtual FrameBuffer)
2. Run Firefox
3. Run the VNC Server

    Xvfb $DISPLAY -extension GLX -screen 0 1024x780x24 &
    $DISPLAY /usr/bin/firefox &
    x11vnc -usepw -display $DISPLAY

3 - X11 Forwarding
------------------

TODO

References
----------

- [Running GUI apps with Docker](http://fabiorehm.com/blog/2014/09/11/running-gui-apps-with-docker/)
- [can you run GUI apps in a docker container?](https://stackoverflow.com/questions/16296753/can-you-run-gui-apps-in-a-docker-container)
- [Running a GUI application in a Docker container](https://linuxmeerkat.wordpress.com/2014/10/17/running-a-gui-application-in-a-docker-container/)
- [Sandboxing proprietary applications with Docker](www.jann.cc/2014/09/06/sandboxing_proprietary_applications_with_docker.html)
