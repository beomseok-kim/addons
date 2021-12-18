# ARG BUILD_FROM=ghcr.io/hassio-addons/base/armv7:11.0.0
ARG BUILD_FROM=python:3
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Copy data for add-on
COPY run.sh /
COPY js /js


# Install requirements for add-on
RUN \
    apk add --no-cache --virtual .build-dependencies \
        g++=10.3.1_git20211027-r0 \
        gcc=10.3.1_git20211027-r0 \
        libc-dev=0.7.2-r3 \
        linux-headers=5.10.41-r0 \
        make=4.3-r0 \
        py3-pip=20.3.4-r1 \
        python3-dev=3.9.7-r4 \
        udev \
        jq \
    \
    && apk add --no-cache \
        nodejs=16.13.1-r0 \
        npm=8.1.3-r0 \
        python3=3.9.7-r4

#    \
#    && apk add --no-cache jq npm make gcc g++ python3 linux-headers udev
#    \
#    && npm init -f
#    \
#    && npm install mqtt \
#    \
#    && npm install serialport --build-from-source

WORKDIR /share
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
