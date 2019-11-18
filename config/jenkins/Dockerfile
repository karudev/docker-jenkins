FROM jenkins/jenkins:lts

LABEL maintainer "Dolyveen Renault, Karudev Informatique, renault@karudev.fr"

ENV JENKINS_HOME_HOTE /home/projects/docker-jenkins/data/jenkins

USER root
RUN addgroup --gid 999 docker
RUN usermod -G docker jenkins

#RUN /usr/local/bin/install-plugins.sh docker-slaves git:3.3.0 \
#   && /usr/local/bin/install-plugins.sh docker-slaves zap:1.0.8

#COPY plugins.txt /usr/share/jenkins/plugins.txt
#RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/plugins.txt

RUN apt-get update && apt-get install -y make git \
	htop \
	apt-transport-https \
        ca-certificates \
	curl \
	gnupg-agent \
	software-properties-common

RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN apt-key fingerprint 0EBFCD88
RUN add-apt-repository \
        "deb [arch=amd64] https://download.docker.com/linux/debian \
	$(lsb_release -cs) \
	stable"
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
#RUN wget -qO- https://deb.nodesource.com/setup_8.x | -E bash -
RUN curl -o /usr/local/bin/n https://raw.githubusercontent.com/visionmedia/n/master/bin/n && chmod +x /usr/local/bin/n && n stable

RUN apt-get update 
RUN apt-get install -y docker-ce \
#		nodejs \
		zip \
                yarn
                
RUN npm -v
RUN curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
RUN chmod +x /usr/local/bin/docker-compose

RUN apt-get install -y vim

#USER jenkins
