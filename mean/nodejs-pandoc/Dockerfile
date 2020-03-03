FROM ubuntu:latest
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y \
    nano \
    curl \
    wget && \
    curl -sL https://deb.nodesource.com/setup_12.x | bash - && \
    apt-get -y install nodejs && \
    apt-get -y install build-essential && \
    apt-get -y install git && \
    apt-get -y install texlive-xetex && \
    apt-get -y clean && \
    apt-get -y autoremove && \
    apt-get -y clean && \
    rm -rf /var/lib/apt/lists/*

RUN wget -O $HOME/pandoc.deb  https://github.com/jgm/pandoc/releases/download/2.9.2/pandoc-2.9.2-1-amd64.deb && \
    dpkg -i $HOME/pandoc.deb && \
    rm $HOME/pandoc.deb

LABEL che:server:3000:ref=nodejs che:server:3000:protocol=http

EXPOSE 3000

WORKDIR /projects

CMD tail -f /dev/null
