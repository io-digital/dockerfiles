# Base image for ubuntu 14.04
FROM iodigital/ubuntu:v1
MAINTAINER io <devops@io.co.za>

# packages we need
RUN cd /tmp && \
	wget http://nodejs.org/dist/node-latest.tar.gz && \
  tar -xvzf node-latest.tar.gz && \
  rm -f node-latest.tar.gz && \
  cd node-v* && \
  ./configure && \
  CXX="g++ -Wno-unused-local-typedefs" make && \
  CXX="g++ -Wno-unused-local-typedefs" make install && \
  cd /tmp && \
  rm -rf /tmp/node-v*

# install npm packages
ONBUILD ADD package.json /app/
ONBUILD RUN npm install
ONBUILD ADD . /app

# Environment vars
ENV NODE_ENV production

# Default work dir
WORKDIR /app

# use npm to start
CMD ["npm", "start"]