ARG BUILD_FROM=ghcr.io/hassio-addons/base/amd64:11.0.0
# ARG BUILD_FROM=python:3
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Copy data for add-on
COPY run.sh /
COPY js /js

WORKDIR /opt

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install requirements for add-on
RUN \
    apk add --no-cache \
        g++ \
        gcc \
        linux-headers \
        make \
        nodejs \
        npm

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
