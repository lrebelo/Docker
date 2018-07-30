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

ENV TERM=xterm

LABEL che:server:3000:ref=nodejs che:server:3000:protocol=http che:server:4000:ref=angular che:server:4000:protocol=http che:server:27017:ref=mongod che:server:27017:protocol=mongo

EXPOSE 3000 4000 27017

WORKDIR /projects

CMD tail -f /dev/null