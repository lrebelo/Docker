FROM ubuntu:latest

ENV TERM=xterm

RUN apt-get update
RUN apt-get install apt-transport-https -y
RUN wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb
RUN rm packages-microsoft-prod.deb
RUN apt-get update
RUN apt-get install dotnet-sdk-3.1 -y
RUN apt-get install dotnet-runtime-3.1 -y

WORKDIR /projects

CMD tail -f /dev/null