# ARG BUILD_FROM=ghcr.io/hassio-addons/base/armv7:11.0.0
ARG BUILD_FROM=python:3
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Copy data for add-on
COPY run.sh /
COPY js /js

WORKDIR /

# Install requirements for add-on
RUN \
    apk add --no-cache nodejs \
    \
    && apk add --no-cache jq npm make gcc g++ python3 linux-headers udev
#    \
#    && npm init -f
#    \
#    && npm install mqtt \
#    \
#    && npm install serialport --build-from-source

WORKDIR /share
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
