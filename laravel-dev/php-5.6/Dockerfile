FROM php:5.6.30-fpm-alpine
LABEL maintainer="Nikolas Silva <nikolas.rsilva@gmail.com>"

RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories
RUN apk update && apk --no-cache add \
  apk-tools=2.10.0-r1 \
  curl \
  git \
  openssh \
  openssl

# Install Composer w/ Prestissimo
ENV COMPOSER_VERSION 1.3.2
RUN curl -sS https://getcomposer.org/installer | php -- \
    --install-dir=/usr/local/bin \
    --filename=composer \
    --version=$COMPOSER_VERSION \
  && composer global require --quiet hirak/prestissimo:^0.3

# Install NodeJS + Yarn
ENV NODE_ALPINE_VERSION 8.11.3-r3
ENV YARN_VERSION v0.21.3
RUN apk --no-cache add npm=$NODE_ALPINE_VERSION \
  && curl -O -sL https://github.com/yarnpkg/yarn/releases/download/$YARN_VERSION/yarn-$YARN_VERSION.tar.gz \
  && mkdir /usr/local/yarn \
  && tar -C /usr/local/yarn --strip-components=1 -zxvf yarn-$YARN_VERSION.tar.gz \
  && rm yarn-$YARN_VERSION.tar.gz

ENV PATH $PATH:/usr/local/yarn/bin
