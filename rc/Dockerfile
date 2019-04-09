FROM openjdk:8-slim


# Replace shell with bash so we can source files
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

RUN apt-get update && apt-get install -y -q --no-install-recommends \
        apt-transport-https \
        build-essential \
        python \
        python-pip \
        ca-certificates \
        curl \
        git \
        libssl-dev \
        libxml2 \
        libxml2-dev \
        libxslt-dev \
        && apt-get autoremove \
        && apt-get clean


ENV NVM_DIR /usr/local/nvm
ENV NODE_VERSION 8.11.3

WORKDIR $NVM_DIR

RUN curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash \
    ; source /root/.bashrc \
    && nvm install $NODE_VERSION \
    && nvm alias default $NODE_VERSION \
    && nvm use default

ENV NODE_PATH $NVM_DIR/versions/node/v$NODE_VERSION/lib/node_modules
ENV PATH      $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH


WORKDIR ~
