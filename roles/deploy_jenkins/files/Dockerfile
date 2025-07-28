FROM jenkins/jenkins:lts-jdk17

USER root

RUN apt-get update && \
    apt-get install -y docker.io && \
    groupmod -g 988 docker && \
    usermod -aG docker jenkins

USER jenkins
