FROM ubuntu:16.04

MAINTAINER ld00000 <lidong9144@163.com>

RUN apt-get autoclean && apt-get --purge -y autoremove && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak
ADD ./163-sources.list /etc/apt/sources.list

RUN apt-get update
RUN echo y | apt-get install wget

RUN apt-get clean \
      && rm -fr /var/lib/apt/lists/* \
        /tmp/* \
        /var/tmp/* \
        /usr/share/man \
        /usr/share/doc \
        /usr/share/doc-base

# ENTRYPOINT ["java", "-version"]
