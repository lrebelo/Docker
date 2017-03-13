FROM codenvy/debian_jre
ENV DEBIAN_FRONTEND noninteractive

RUN sudo apt-get update && sudo apt-get install -y \
    echo "deb http://repo.mongodb.org/apt/debian jessie/mongodb-org/3.4 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list && \
    sudo apt-get update && \
    sudo apt-get -y install mongodb-org && \
    sudo service mongod start && \
    sudo npm install -g @angular/cli && \
    sudo npm install express-generator -g && \
    sudo npm install pm2@latest -g && \
    sudo apt-get -y install nano && \
    sudo apt-get -y clean && \
    sudo apt-get -y autoremove && \
    sudo apt-get -y clean && \
    sudo rm -rf /var/lib/apt/lists/*

LABEL che:server:27017:ref=mongod che:server:27017:protocol=mongo

EXPOSE 27017

WORKDIR /projects

CMD tail -f /dev/null
