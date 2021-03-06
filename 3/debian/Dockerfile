FROM python:3.6.6-slim-stretch

LABEL maintainer="Jose Truyol <jose@namku.cl>"

ARG RUNTIME_DEPS='ca-certificates libpng-dev libjpeg-dev libgif-dev libopenblas-dev libx11-dev liblapack-dev liblapacke-dev'
ARG BUILD_DEPS='apt-utils wget unzip cmake build-essential pkg-config'
ARG LIB_PREFIX='/usr/local'
ARG VERSION='19.13'

ENV DLIB_VERSION=${VERSION} \
    LIB_PREFIX=${LIB_PREFIX} \
    DLIB_INCLUDE_DIR='$LIB_PREFIX/include' \
    DLIB_LIB_DIR='$LIB_PREFIX/lib'

RUN echo "Dlib: ${DLIB_VERSION}" \
    && apt-get update && apt-get install -y ${BUILD_DEPS} ${RUNTIME_DEPS} --no-install-recommends \
    && wget -q https://github.com/davisking/dlib/archive/v${DLIB_VERSION}.zip -O dlib.zip \
    && dlib_cmake_flags="-D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=$LIB_PREFIX \
    -D DLIB_NO_GUI_SUPPORT=OFF \
    -D DLIB_USE_BLAS=ON \
    -D DLIB_GIF_SUPPORT=ON \
    -D DLIB_PNG_SUPPORT=ON \
    -D DLIB_JPEG_SUPPORT=ON \
    -D DLIB_USE_CUDA=OFF" \
    && unzip -qq dlib.zip \
    && mv dlib-${DLIB_VERSION} dlib \
    && rm dlib.zip \
    && cd dlib \
    && mkdir -p build \
    && cd build \
    && cp /usr/include/lapacke*.h /usr/include/openblas/ \
    && cmake $dlib_cmake_flags .. \
    && make -j $(getconf _NPROCESSORS_ONLN) \
    && cd /dlib/build \
    && make install \
    && cp /dlib/dlib/*.txt $LIB_PREFIX/include/dlib/ \
    && cd /dlib \
    && python setup.py install \
    && cd / \
    && rm -rf /dlib \
    && apt-get purge -y --auto-remove $BUILD_DEPS \
    && apt-get autoremove -y --purge \
    && apt-get install -y $RUNTIME_DEPS --no-install-recommends \
    && rm -rf /var/lib/apt/lists/* /usr/share/man /usr/local/share/man /tmp/*

CMD ["python3"]
