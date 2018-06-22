FROM openjdk:8u171-jdk-alpine3.7

ENV SBT_VERSION 1.1.6

RUN apk add --no-cache bash

RUN apk --no-cache --virtual .build-deps add curl && \
    curl -sL "https://piccolo.link/sbt-$SBT_VERSION.tgz" | tar -zxC /usr/local && \
    ln -s /usr/local/sbt/bin/sbt /usr/local/bin/sbt && \
    chmod 0755 /usr/local/bin/sbt && \
    apk del .build-deps

COPY build.sbt /app/

COPY project /app/project

RUN cd app && sbt -v update

RUN rm -rf /app
