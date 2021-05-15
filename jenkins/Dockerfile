FROM jenkins/jenkins:lts-alpine

USER root

RUN apk update && apk upgrade \
    && apk add --no-cache python3 py3-pip \
    && ln -sf python3 /usr/bin/python

RUN pip install -U mock \
    nose \
    coverage \
    prospector

USER jenkins

# Web
EXPOSE 8080

# Jira
EXPOSE 50000