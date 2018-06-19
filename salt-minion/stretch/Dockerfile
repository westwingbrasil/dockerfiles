FROM debian:stretch
LABEL maintainer "Nikolas Silva <nikolas.rsilva@gmail.com>"

ENV SALT_VERSION=2017.7.2

RUN apt-get update -y && apt-get install -y wget gnupg2
RUN wget -q -O - https://repo.saltstack.com/apt/debian/9/amd64/archive/$SALT_VERSION/SALTSTACK-GPG-KEY.pub | apt-key add - \
 && echo "deb http://repo.saltstack.com/apt/debian/9/amd64/archive/$SALT_VERSION stretch main" > /etc/apt/sources.list.d/saltstack.list \
 && apt-get update -y && apt-get install -y \
	salt-common \
	salt-minion

VOLUME ["/srv/salt", "/srv/pillar"]

ENTRYPOINT salt-minion