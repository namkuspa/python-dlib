FROM python:3.6.6-alpine

LABEL maintainer="Jose Truyol <jose@namku.cl>"

ENV CC=/usr/bin/gcc \
    CXX=/usr/bin/g++
# Instalando DLIB en Alpine
RUN apk update \
    && apk add -U \
       # --virtual .runtime-dependencies \
       openblas \
       jpeg \
       libpng \
       giflib \
    && apk add -U \
       --virtual .build-dependencies \
       git \
       cmake \
       g++ \
       make \
       jpeg-dev \
       libpng-dev \
        giflib-dev \
       openblas-dev \
       ca-certificates wget
RUN pip install dlib numpy scipy  --no-cache-dir
RUN apk del .build-dependencies \
    && rm -rf /var/cache/apk/*
ENTRYPOINT ["python3"]
