FROM eclipse/stack-base:ubuntu

ENV TERM=xterm

RUN sudo apt-get install apt-transport-https
RUN sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
RUN echo "deb https://download.mono-project.com/repo/ubuntu stable-xenial main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
RUN sudo apt-get update
RUN sudo apt-get install mono-complete -y

WORKDIR /projects

CMD tail -f /dev/null