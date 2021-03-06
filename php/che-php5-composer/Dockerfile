FROM codenvy/debian_jre
ENV DEBIAN_FRONTEND noninteractive

# install php with a set of most widely used extensions
RUN sudo apt-get update && sudo apt-get install -y \
    nano \
    apache2 \
    php5 \
    php5-mhash \
    php5-mcrypt \
    php5-curl \
    php5-cli \
    php5-mysql \
    php5-gd \
    libapache2-mod-php5 \
    php5-cli \
    php5-json \
    php5-cgi \
    php5-sqlite && \
    sudo sed -i 's/\/var\/www\/html/\/projects/g'  /etc/apache2/sites-available/000-default.conf && \
    sudo sed -i 's/None/All/g' /etc/apache2/apache2.conf && \
    sudo sed -i 's/\/var\/www/\/projects/g'  /etc/apache2/apache2.conf && \
    echo "ServerName localhost" | sudo tee -a /etc/apache2/apache2.conf && \
    sudo a2enmod rewrite && \
    curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer && \
    sudo -E bash -c "apt-get -y --no-install-recommends install mysql-server" && \
    sudo apt-get clean && \
    sudo apt-get -y autoremove && \
    sudo apt-get -y clean && \
    sudo rm -rf /var/lib/apt/lists/* && \
    sudo sed -i.bak 's/127.0.0.1/0.0.0.0/g' /etc/mysql/my.cnf && \
    sudo service mysql restart && \
    sudo mysql -uroot -e "GRANT ALL PRIVILEGES ON *.* TO 'root'@'%'; FLUSH PRIVILEGES;" && \
    sudo service mysql restart

# label is used in Servers tab to display mapped port for Apache process on 80 port in the container
LABEL che:server:80:ref=apache2 che:server:80:protocol=http

EXPOSE 80 3306

WORKDIR /projects

CMD tail -f /dev/null
