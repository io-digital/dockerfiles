FROM ubuntu:12.04
MAINTAINER Barry Botha <barry@io.co.za>

RUN echo "Installing Base Packages"
RUN apt-get update && apt-get upgrade -y
RUN apt-get install apt-utils python-software-properties git openssh-client wget -y

RUN echo "Installing Jenkins"
RUN wget -q -O - http://pkg.jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -
RUN echo deb http://archive.ubuntu.com/ubuntu precise universe >> /etc/apt/sources.list
RUN echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list
RUN apt-get update
RUN apt-get install -y jenkins

RUN echo "Starting Jenkins"
RUN /etc/init.d/jenkins start

RUN echo "Setting up SSH credentials"
RUN sudo -u jenkins ssh-keygen -f id_rsa -t rsa -N ''
RUN ssh-keygen -f /var/lib/jenkins/.ssh/known_hosts -H -F github.com | grep -q found || ssh-keyscan -H github.com > /var/lib/jenkins/.ssh/known_hosts
RUN ssh-keygen -f /var/lib/jenkins/.ssh/known_hosts -H -F bitbucket.com | grep -q found || ssh-keyscan -H bitbucket.com > /var/lib/jenkins/.ssh/known_hosts

RUN echo "SSH Public Key Generated:"
RUN cat /var/lib/jenkins/.ssh/id_rsa.pub

RUN echo "Run Command:"
RUN echo "docker run -p 127.0.0.1:8080:8080 -v /var/lib/jenkins:/var/lib/jenkins -d io-digital/jenkins"

EXPOSE 8080