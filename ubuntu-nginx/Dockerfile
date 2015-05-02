FROM ubuntu:14.04
MAINTAINER io <devops@io.co.za>

# Base image for ubuntu 14.04
FROM iodigital/ubuntu:v1

# Install nginx
RUN add-apt-repository -y ppa:nginx/stable && \
    apt-get update && \
    apt-get install -y nginx && \
    rm -rf /var/lib/apt/lists/* && \
    echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
    chown -R www-data:www-data /var/lib/nginx

# Default work dir
WORKDIR /etc/nginx

# Default cmd
CMD ["nginx"]

# Expose Ports
EXPOSE 80
EXPOSE 443