FROM rebeloml/nodejs:latest
ENV DEBIAN_FRONTEND noninteractive

RUN sudo npm install -g @angular/cli && \

LABEL che:server:4000:ref=angular2 che:server:4000:protocol=http

EXPOSE 4000

WORKDIR /projects

CMD tail -f /dev/null
