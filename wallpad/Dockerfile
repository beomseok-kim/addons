ARG BUILD_FROM=ghcr.io/hassio-addons/base/amd64:11.0.0
# ARG BUILD_FROM=python:3
FROM ${BUILD_FROM}

ENV LANG C.UTF-8

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install requirements for add-on


출처: https://neet.tistory.com/entry/Alpine-linux-ERROR-unsatisfiable-constraints-docker-missing-required-by-worlddocker-오류-해결방법 [자택경비대]

RUN \
    echo "http://dl-cdn.alpinelinux.org/alpine/latest-stable/community" >> /etc/apk/repositories \
    && apk update \
    && apk add --no-cache jq npm make gcc g++ python3 linux-headers udev
#    \
#    && npm init -f
#    \
#    && npm install mqtt \
#    \
#    && npm install serialport --build-from-source

# Copy data for add-on
COPY run.sh /
COPY js /js

WORKDIR /share
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
