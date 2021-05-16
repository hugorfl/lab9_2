FROM jenkins/jenkins:lts-alpine

USER root

RUN apk update && apk upgrade \
    && apk add --no-cache python3 py3-pip \
    && ln -sf python3 /usr/bin/python \
    && apk add build-base flex bison gnu-libiconv make cmake

# https://www.doxygen.nl/manual/install.html
RUN git clone https://github.com/doxygen/doxygen.git \
    && cd doxygen && git checkout Release_1_9_1 \
    && mkdir build && cd build \
    && cmake -G "Unix Makefiles" .. && make && make install \
    && ln -sf /usr/local/bin/doxygen /usr/bin/doxygen \
    && rm -rf doxygen

RUN pip install -U mock \
    nose \
    coverage \
    prospector

USER jenkins

# Web
EXPOSE 8080

# Agent
EXPOSE 50000