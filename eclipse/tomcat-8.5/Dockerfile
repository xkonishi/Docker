FROM centos:7.5.1804

# locale
RUN localedef -i ja_JP -f UTF-8 ja_JP.UTF-8
RUN echo 'LANG="ja_JP.UTF-8"' >  /etc/locale.conf
ENV LANG ja_JP.UTF-8

# X Window System
#RUN yum -y groupinstall "X Window System"
ENV DISPLAY host.docker.internal:0.0

# Java
WORKDIR /tmp
COPY jre/jre-8u181-linux-x64.rpm ./
RUN yum -y localinstall ./jre-8u181-linux-x64.rpm

ENV JAVA_HOME /usr/java/default
ENV JAVA_VERSION 8u181

# Eclipse
RUN adduser -d /home/eclipse eclipse
RUN echo "eclipse:eclipse" | chpasswd
ADD eclipse-4.11/eclipse-jee-2019-03-R-linux-gtk-x86_64.tar.gz /home/eclipse/eclipse-4.11

# Tomcat
ADD tomcat/apache-tomcat-8.5.32.tar.gz /usr/local

ENV TOMCAT_VERSION 8.5.32
ENV CATALINA_HOME /usr/local/apache-tomcat-8.5.32
ENV PATH ${CATALINA_HOME}/bin;${PATH}

# Tomcat start up
EXPOSE 8080 22
CMD ${CATALINA_HOME}/bin/catalina.sh run
