FROM ubuntu:12.04
MAINTAINER Barry Botha <barry@io.co.za>

RUN apt-get update && apt-get upgrade -y
RUN apt-get install apt-utils python-software-properties git -y
RUN apt-get install -y openssh-client curl 

RUN curl http://pkg.jenkins-ci.org/debian/jenkins-ci.org.key | apt-key add -
RUN echo deb http://archive.ubuntu.com/ubuntu precise universe >> /etc/apt/sources.list
RUN echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list
RUN apt-get update
RUN mkdir /var/run/jenkins
RUN apt-get install -y jenkins

ADD run /usr/local/bin/
EXPOSE 8080
VOLUME ["/var/lib/jenkins"]
CMD ["/usr/local/bin/run"]