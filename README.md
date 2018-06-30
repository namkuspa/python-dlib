# python-dlib
[![Automated Build](https://img.shields.io/docker/automated/namkuspa/python-dlib.svg)](https://hub.docker.com/r/namkuspa/python-dlib/)
[![Build Status](https://img.shields.io/docker/build/namkuspa/python-dlib.svg)](https://hub.docker.com/r/namkuspa/python-dlib/)


| Tag   | Size | Layers |
|-------|------|--------|
| 3.6.6 | [![MicroBadger Size (tag)](https://img.shields.io/microbadger/image-size/namkuspa/python-dlib/3.6.6.svg)](https://hub.docker.com/r/namkuspa/python-opencv-dlib/)    | [![MicroBadger Layers (tag)](https://img.shields.io/microbadger/layers/namkuspa/python-dlib/3.6.6.svg)](https://hub.docker.com/r/namkuspa/python-dlib/)|


## ¿Cómo usar?
```console
$ docker run --rm -it namkuspa/python-opencv-dlib:3.6.6
Python 3.6.6 (default, Jun 27 2018, 22:32:42) 
[GCC 6.3.0 20170516] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import dlib
>>> dlib.__version__
'19.13.0'
```