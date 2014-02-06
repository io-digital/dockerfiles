FROM ubuntu:12.04
MAINTAINER Barry Botha <barry@io.co.za>

# Installing Base Packages

RUN apt-get update && apt-get upgrade -y
RUN apt-get install apt-utils python-software-properties git openssh-client wget -y

# Installing Jenkins

RUN wget -q -O - http://pkg.jenkins-ci.org/debian/jenkins-ci.org.key | apt-key add -
RUN echo deb http://archive.ubuntu.com/ubuntu precise universe >> /etc/apt/sources.list
RUN echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list
RUN apt-get update
RUN apt-get install -y jenkins

# Starting Jenkins

RUN /etc/init.d/jenkins start

# Setting up SSH credentials

RUN su -c "ssh-keygen -f id_rsa -t rsa -N ''" jenkins
RUN su -c "ssh-keygen -f /var/lib/jenkins/.ssh/known_hosts -H -F github.com | grep -q found || ssh-keyscan -H github.com > /var/lib/jenkins/.ssh/known_hosts" jenkins
RUN su -c "ssh-keygen -f /var/lib/jenkins/.ssh/known_hosts -H -F bitbucket.com | grep -q found || ssh-keyscan -H bitbucket.com > /var/lib/jenkins/.ssh/known_hosts" jenkins

# SSH Public Key Generated
# Run Command:
# docker run -p 8080:8080 -v /var/lib/jenkins:/var/lib/jenkins -d io-digital/jenkins

EXPOSE 8080