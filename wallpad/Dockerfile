#ARG BUILD_FROM="alpine:latest"
ARG BUILD_FROM="python:3"
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Copy data for add-on
COPY run.sh /
COPY js /js
# Copy Node-RED package.json
COPY package.json /opt/

# Set workdir
WORKDIR /opt

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install requirements for add-on
#RUN apk add --no-cache nodejs
#RUN apk add --no-cache jq npm make gcc g++ python3 linux-headers udev
# RUN npm init -f
# RUN npm install mqtt
#RUN npm install serialport --build-from-source=serialport 

RUN \
    apk add --no-cache \
        g++=10.3.1_git20211027-r0 \
        gcc=10.3.1_git20211027-r0 \
        libc-dev=0.7.2-r3 \
        linux-headers=5.10.41-r0 \
        make=4.3-r0 \
        py3-pip=20.3.4-r1 \
        udev \
        jq \
        git=2.34.1-r0 \
        nodejs=16.13.1-r0 \
        npm=8.1.3-r0 \
        python3=3.9.7-r4 \
RUN \
    npm config set unsafe-perm true \
    \
    && npm install \
        --no-audit \
        --no-optional \
        --no-update-notifier \
        --only=production \
        --unsafe-perm \
    \
    && npm cache clear --force

WORKDIR /share
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
