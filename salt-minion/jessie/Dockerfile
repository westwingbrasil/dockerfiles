FROM debian:jessie

LABEL maintainer "Westwing Dev Team <devs@westwing.com.br>"

RUN apt-get update -y && apt-get install -y \
    apt-transport-https \
    wget \
    curl \
    gnupg2 \
    locales

RUN locale-gen en_US.UTF-8

RUN wget -O - https://repo.saltstack.com/apt/debian/8/amd64/latest/SALTSTACK-GPG-KEY.pub | apt-key add - \
    && echo "deb http://repo.saltstack.com/apt/debian/8/amd64/latest jessie main" > /etc/apt/sources.list.d/saltstack.list \
    && apt-get update -y && apt-get install -y salt-minion

ENV LANG C.UTF-8
ENV LANGUAGE C.UTF-8
ENV LC_ALL C.UTF-8

VOLUME ["/srv/salt", "/srv/pillar"]

ENTRYPOINT salt-minion