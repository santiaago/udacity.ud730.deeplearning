# udacity.ud730.deeplearning

deep learning course by udacity

Over this readme the name of the image will be `udacity`.
You can name containers by using the `--name`

#### run assignments:
~~~
docker run --name udacity -p 8888:8888 -it --rm b.gcr.io/tensorflow-udacity/assignments
~~~

#### find virtual machine's IP:
~~~
$ docker-machine.exe ip default
192.168.99.xxx
~~~

go to `http://192.168.99.xxx:8888`

#### how to login into docker hub
~~~
$ docker login https://index.docker.io/v1/
~~~

issues with login in windows? check this out [DockerToolbox in windows Login/push doesnt works properly (With a workaround)](https://github.com/docker/hub-feedback/issues/473)

#### save current docker

0- login to docker hub
1- To get current container names do `docker ps`
2- commit container
~~~
docker commit udacity user/repository
~~~
3- push the container
~~~
docker push index.docker.io/username/repository
~~~

#### access docker container through a terminal.

~~~
docker exec -it udacity bash
~~~

#### run container without loosing your data

~~~
docker run --name udacity -p 8888:8888 -v /c/Users/username/yourpathto/assignments/:/notebooks -it --rm b.gcr.io/tensorflow-udacity/assignments
~~~

**Note**: on windows machines you cannot mount volumes outside of `c:/Users/username` because
[reasons](https://docs.docker.com/engine/userguide/dockervolumes/#mount-a-host-directory-as-a-data-volume)

> If you are using Docker Machine on Mac or Windows, your Docker daemon has only limited access to your OS X or Windows filesystem. Docker Machine tries to auto-share your /Users (OS X) or C:\Users (Windows) directory.







