FROM ubuntu:latest
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y \
    nano \
    curl && \
    curl -sL https://deb.nodesource.com/setup_12.x | bash - && \
    apt-get -y install nodejs && \
    apt-get -y install build-essential && \
    apt-get -y clean && \
    apt-get -y autoremove && \
    apt-get -y git && \
    apt-get -y clean && \
    rm -rf /var/lib/apt/lists/*

LABEL che:server:3000:ref=nodejs che:server:3000:protocol=http

EXPOSE 3000

WORKDIR /projects

CMD tail -f /dev/null
