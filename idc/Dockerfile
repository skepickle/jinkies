FROM ubuntu:16.04

RUN DEBIAN_FRONTEND=noninteractive set -x \
    && apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends \
          git groovy2 ssh vim

RUN mkdir /root/.ssh
RUN chmod 700 /root/.ssh

COPY .ssh/config /root/.ssh/
COPY .ssh/github /root/.ssh/

RUN chmod 600 /root/.ssh/github

WORKDIR /root

RUN ssh -n -oStrictHostKeyChecking=no git@github.com ; true
RUN git clone git@github.com:skepickle/jinkies.git

WORKDIR /root/jinkies
