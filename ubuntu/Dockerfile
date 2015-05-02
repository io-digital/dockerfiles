# Base image for ubuntu 14.04
FROM ubuntu:14.04
MAINTAINER io <devops@io.co.za>

# packages we need
RUN apt-get update && \
	apt-get -y upgrade && \
	apt-get install -y build-essential && \
	apt-get install -y software-properties-common && \
	apt-get install -y python python-dev python-setuptools python-pip python-virtualenv unzip && \
	apt-get install -y curl git wget aptitude htop iftop && \
	rm -rf /var/lib/apt/lists/*

# Environment vars
ENV HOME /root

# Default work dir
WORKDIR /root

# Default command
CMD ["bash"]