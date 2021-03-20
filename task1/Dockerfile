FROM ubuntu:latest

ENV JAVA_VER 8.0.275.open-adpt
ENV SCALA_VER 2.12.13

RUN mkdir -pv /persist
VOLUME /persist

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y zip unzip curl sudo

RUN curl -fsSL https://deb.nodesource.com/setup_15.x | sudo -E bash - && sudo apt-get install -y nodejs
EXPOSE 3000

RUN curl -s "https://get.sdkman.io" | bash
RUN rm /bin/sh && ln -s /bin/bash /bin/sh
SHELL ["/bin/bash", "-c"]
RUN source "$HOME/.sdkman/bin/sdkman-init.sh" && \
    sdk list java && \
    sdk install java ${JAVA_VER} && \
    sdk list scala && \
    sdk install scala ${SCALA_VER} && \
    sdk install sbt
EXPOSE 8080
