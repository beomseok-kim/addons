#ARG BUILD_FROM=alpine:3.9
ARG BUILD_FROM
FROM ${BUILD_FROM}

ENV LANG C.UTF-8

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install requirements for add-on

RUN apk add --no-cache jq npm make gcc g++ python3 linux-headers udev

WORKDIR /usr/app
RUN \
    npm init -g \
    \
    && npm install -g mqtt \
    \
    && npm install -g serialport --build-from-source

# Copy data for add-on
COPY run.sh /
COPY js /js

# WORKDIR /share
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
