# udacity.ud730.deeplearning

deep learning course by udacity

Over this readme the name of the image will be `udacity`.
You can name containers by using the `--name`

* [run-assignments](#run-assignments)
* [find virtual machines ip](#find-virtual-machines-ip)
* [how to login into docker hub](#how-to-login-into-docker-hub)
* [save current docker](#save-current-docker)
* [access docker container through a terminal](#access-docker-container-through-a-terminal)

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

1. login to docker hub
2. To get current container names do `docker ps`
3. commit container
~~~
docker commit udacity user/repository
~~~
4. push the container
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

#### memory errors

you might be getting memory errors like the following:

~~~~
---------------------------------------------------------------------------
MemoryError                               Traceback (most recent call last)
<ipython-input-8-5158e101f707> in <module>()
     37   print('Labels:', labels.shape)
     38   return dataset, labels
---> 39 train_dataset, train_labels = load(train_folders, 450000, 550000)
     40 test_dataset, test_labels = load(test_folders, 18000, 20000)

<ipython-input-8-5158e101f707> in load(data_folders, min_num_images, max_num_images)
     34   print('Full dataset tensor:', dataset.shape)
     35   print('Mean:', np.mean(dataset))
---> 36   print('Standard deviation:', np.std(dataset))
     37   print('Labels:', labels.shape)
~~~~

Try changing the RAM you provide to your docker container.
To do this use the `-m` or `--memory`

example:
~~~
docker run --name udacity --memory 4096m -p 8888:8888 -v /c/Users/username/yourpathto/assignments/:/notebooks -it --rm b.gcr.io/tensorflow-udacity/assignments
~~~





