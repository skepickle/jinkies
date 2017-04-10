FROM ubuntu:16.04

RUN DEBIAN_FRONTEND=noninteractive set -x \
    && apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends \
          git groovy2 ssh vim

COPY .gitconfig /root/

RUN mkdir /root/.ssh
RUN chmod 700 /root/.ssh

COPY .ssh/config /root/.ssh/
COPY .ssh/github /root/.ssh/

RUN chmod 600 /root/.ssh/github

WORKDIR /root

RUN ssh -n -oStrictHostKeyChecking=no git@github.com ; true

WORKDIR /root/jinkies

CMD git clone --branch ${GIT_BRANCH} git@github.com:skepickle/jinkies.git /root/jinkies ; /bin/bash
