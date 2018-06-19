FROM debian:jessie

LABEL maintainer "Westwing Dev Team <devs@westwing.com.br>"

RUN apt-get update -y && apt-get install -y wget gnupg2
RUN wget -O - https://repo.saltstack.com/apt/debian/8/amd64/latest/SALTSTACK-GPG-KEY.pub | apt-key add - \
    && echo "deb http://repo.saltstack.com/apt/debian/8/amd64/latest jessie main" > /etc/apt/sources.list.d/saltstack.list \
    && apt-get update -y && apt-get install -y salt-minion

VOLUME ["/srv/salt", "/srv/pillar"]

ENTRYPOINT salt-minion