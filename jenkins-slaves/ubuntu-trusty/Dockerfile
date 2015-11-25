FROM achaussier/ubuntu-trusty-ssh:v1
MAINTAINER Alexandre Chaussier <a.chaussier@infopen.pro>

# Install base packages
RUN apt-get update && \
    apt-get install -y curl=7.35.0*

# Get gosu GPG key
RUN gpg --keyserver ha.pool.sks-keyservers.net \
        --recv-keys B42F6819007F00F88E364FD4036A9C25BF357DD4

# Install Gosu
ENV GOSU_VERSION 1.7
RUN curl -o /usr/local/bin/gosu -SL "https://github.com/tianon/gosu/releases/download/${GOSU_VERSION}/gosu-$(dpkg --print-architecture)" \
 && curl -o /usr/local/bin/gosu.asc -SL "https://github.com/tianon/gosu/releases/download/${GOSU_VERSION}/gosu-$(dpkg --print-architecture).asc" \
 && gpg --verify /usr/local/bin/gosu.asc \
 && rm /usr/local/bin/gosu.asc \
 && chmod +x /usr/local/bin/gosu

# Create user for Jenkins
RUN useradd -m \
            -s /bin/bash \
            jenkins

# Set password for jenkins user
RUN echo "jenkins:jenkins" | chpasswd

