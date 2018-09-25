FROM eclipse/stack-base:ubuntu


RUN echo "deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main" | sudo tee /etc/apt/sources.list.d/ansible.list
RUN sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
RUN sudo apt-get update 
RUN sudo apt-get install ansible -y

RUN sudo apt-get update && sudo apt-get install -y \
    nano \
    curl && \
    curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash - && \
    sudo apt-get -y install nodejs && \
    sudo apt-get -y install build-essential && \
    sudo apt-get -y clean && \
    sudo apt-get -y autoremove && \
    sudo apt-get -y clean && \
    sudo rm -rf /var/lib/apt/lists/*

RUN sudo npm install -g @angular/cli

RUN sudo npm install -g pm2

RUN sudo mkdir /data && sudo mkdir /data/db
RUN echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list && \
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4 && \
    sudo apt-get update && \
    sudo apt-get -y install mongodb-org && \
    sudo apt-get -y install nano && \
    sudo apt-get -y clean && \
    sudo apt-get -y autoremove && \
    sudo apt-get -y clean && \
    sudo rm -rf /var/lib/apt/lists/*
RUN sudo mongod &

RUN sudo apt-get update
RUN sudo apt-get install apt-transport-https -y
RUN sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
RUN echo "deb https://download.mono-project.com/repo/ubuntu stable-xenial main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
RUN sudo apt-get update
RUN sudo apt-get install mono-complete -y

RUN sudo apt-get install -y --no-install-recommends supervisor x11vnc xvfb net-tools blackbox rxvt-unicode xfonts-terminus libxi6 libgconf-2-4


RUN sudo mkdir -p /opt/noVNC/utils/websockify && \
    wget -qO- "http://github.com/kanaka/noVNC/tarball/master" | sudo tar -zx --strip-components=1 -C /opt/noVNC && \
    wget -qO- "https://github.com/kanaka/websockify/tarball/master" | sudo tar -zx --strip-components=1 -C /opt/noVNC/utils/websockify

ADD index.html /opt/noVNC/

RUN sudo mkdir -p /etc/X11/blackbox && \
    echo "[begin] (Blackbox) \n [exec] (Terminal)     {urxvt -fn "xft:Terminus:size=12"} \n [end]" | sudo tee -a /etc/X11/blackbox/blackbox-menu

ADD supervisord.conf /opt/

CMD /usr/bin/supervisord -c /opt/supervisord.conf && tail -f /dev/null


LABEL che:server:3000:ref=nodejs che:server:3000:protocol=http che:server:4000:ref=angular che:server:4000:protocol=http che:server:27017:ref=mongod che:server:27017:protocol=mongo che:server:6080:ref=VNC che:server:6080:protocol=http

EXPOSE 3000 4000 27017 6080

WORKDIR /projects

CMD tail -f /dev/null