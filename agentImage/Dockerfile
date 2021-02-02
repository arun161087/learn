FROM jenkins/inbound-agent
LABEL maintainer='Arun K Singh'
# https://linktr.ee/arunksingh
ENV HELM_VERSION 3.5.0
USER root
# Install Docker
RUN apt-get install -y \
      apt-transport-https \
      ca-certificates \
      curl \
      gnupg2 \
      jq \
      software-properties-common \
    && curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - \
    && add-apt-repository \
      "deb [arch=amd64] https://download.docker.com/linux/debian \
      $(lsb_release -cs) \
      stable" \
    && apt-get update \
    && apt-get -y install docker-ce
RUN usermod -aG docker jenkins
RUN newgrp docker

# install helm
RUN mkdir /tmp/helm                                      \
  && cd /tmp/helm                                        \
  && curl -s https://get.helm.sh/helm-v${HELM_VERSION}-linux-amd64.tar.gz  | tar zxvf - \
  && cp /tmp/helm/linux-amd64/helm /usr/local/bin/helm   \
  && chmod +x /usr/local/bin/helm                        \
  && rm -rf /tmp/helm

USER jenkins
