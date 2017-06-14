FROM jenkins:2.46.3

LABEL maintainer "Dolyveen Renault, Karudev Informatique, renault@karudev.fr"

ENV JENKINS_HOME_HOTE /srv/docker-jenkins/data/jenkins

USER root
RUN addgroup --gid 999 docker
RUN usermod -G docker jenkins

RUN /usr/local/bin/install-plugins.sh docker-slaves git:3.3.0 \
   && /usr/local/bin/install-plugins.sh docker-slaves zap:1.0.8


USER jenkins
