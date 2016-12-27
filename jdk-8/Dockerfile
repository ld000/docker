FROM ubuntu:14.04

MAINTAINER ld00000 <lidong9144@163.com>

RUN apt-get autoclean && apt-get --purge -y autoremove && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak
ADD ./163-sources.list /etc/apt/sources.list

RUN apt-get update
RUN echo y | apt-get install wget

# jdk
ENV VERSION 8
ENV UPDATE 111
ENV BUILD 14

ENV JAVA_HOME /usr/lib/jvm/java-${VERSION}-oracle
ENV JRE_HOME ${JAVA_HOME}/jre

RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" \
    -P /tmp \
    http://download.oracle.com/otn-pub/java/jdk/"${VERSION}"u"${UPDATE}"-b"${BUILD}"/jdk-"${VERSION}"u"${UPDATE}"-linux-x64.tar.gz

RUN cd /tmp && tar -zxvf jdk-"${VERSION}"u"${UPDATE}"-linux-x64.tar.gz && \
    mkdir -p /usr/lib/jvm && mv /tmp/jdk1.${VERSION}.0_${UPDATE} "${JAVA_HOME}" && \
    rm -rf /tmp/*

RUN update-alternatives --install "/usr/bin/java" "java" "${JRE_HOME}/bin/java" 1 && \
    update-alternatives --install "/usr/bin/javac" "javac" "${JAVA_HOME}/bin/javac" 1 && \
    update-alternatives --set java "${JRE_HOME}/bin/java" && \
    update-alternatives --set javac "${JAVA_HOME}/bin/javac"

RUN apt-get clean \
      && rm -fr /var/lib/apt/lists/* \
        /tmp/* \
        /var/tmp/* \
        /usr/share/man \
        /usr/share/doc \
        /usr/share/doc-base

# ENTRYPOINT ["java", "-version"]
