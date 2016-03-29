# DOCKER-VERSION 1.10.3
# VERSION        0.1
# SOURCE         https://github.com/mesosinfo/marathon

FROM ubuntu:14.04
MAINTAINER Yong Zhang<zhangyong.net@qq.com>

# Install dependancies
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv E56151BF && \
echo deb http://repos.mesosphere.io/ubuntu trusty main > /etc/apt/sources.list.d/mesosphere.list && \
apt-get update

RUN apt-get -y install marathon=0.10.1-1.0.416.ubuntu1404 mesos=0.28.0-2.0.16.ubuntu1404

EXPOSE 8080
WORKDIR /opt/marathon
CMD ["--help"]
ENTRYPOINT ["/opt/marathon/bin/start"]
