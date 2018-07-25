FROM jgoerzen/debian-base-standard:latest

RUN sudo cat "deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main" >> /etc/apt/sources.list 
RUN sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
RUN sudo apt-get update
RUN sudo apt-get install ansible