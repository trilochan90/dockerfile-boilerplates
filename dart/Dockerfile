FROM ubuntu
ARG VCS_REF
ARG BUILD_DATE

LABEL maintainer="Gautham Prakash <github.com/gauthamp10>"
LABEL org.label-schema.build-date=$BUILD_DATE
LABEL org.label-schema.vcs-url="https://github.com/gauthamp10/dockerfile-boilerplates"
LABEL org.label-schema.vcs-ref=$VCS_REF

RUN apt-get update && \
    apt-get install -y curl && \
    apt-get install -y gnupg2 && \
    apt-get clean;

RUN apt-get update && \
    apt-get install apt-transport-https && \
    apt-get install wget && \
    sh -c 'wget -qO- https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -' && \
    sh -c 'wget -qO- https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list'

RUN apt-get update && \
    apt-get install -y dart && \
    apt-get clean && \
    apt-get autoremove && \
    mkdir app;
    
RUN export PATH="$PATH:/usr/lib/dart/bin" && \
    echo 'export PATH="$PATH:/usr/lib/dart/bin"' >> ~/.profile

COPY app/app.dart /app
WORKDIR /app

CMD ["dart","./app.dart"]
