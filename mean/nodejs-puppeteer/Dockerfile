FROM ubuntu:latest
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y \
    nano \
    curl && \
    curl -sL https://deb.nodesource.com/setup_12.x | bash - && \
    apt-get -y install nodejs && \
    apt-get -y install build-essential && \
    apt-get -y install git && \
    apt-get -y install libx11-xcb-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxi6 libxtst6 libglib2.0-0 libnss3 libcups2 libxss1 libxrandr2 && \
    apt-get -y install chromium-browser && \
    apt-get -y clean && \
    apt-get -y autoremove && \
    apt-get -y clean && \
    rm -rf /var/lib/apt/lists/* && \
    mkdir /home/runuser && \
    groupadd -r runuser && useradd -r -g runuser -G audio,video runuser -b /home/runuser && \
    chown -R runuser:runuser /home/runuser && \
    mkdir /projects && \
    chown -R runuser:runuser /projects

LABEL che:server:3000:ref=nodejs che:server:3000:protocol=http

EXPOSE 3000

WORKDIR /projects

USER runuser

CMD tail -f /dev/null
