FROM centos:7.5.1804

# locale
RUN localedef -i ja_JP -f UTF-8 ja_JP.UTF-8
RUN echo 'LANG="ja_JP.UTF-8"' >  /etc/locale.conf
ENV LANG ja_JP.UTF-8

# X Window System
#RUN yum -y groupinstall "X Window System"
ENV DISPLAY host.docker.internal:0.0

# Java
#WORKDIR /tmp
#COPY jre/jre-8u181-linux-x64.rpm ./
#RUN yum -y localinstall ./jre-8u181-linux-x64.rpm

#ENV JAVA_HOME /usr/java/default
#ENV JAVA_VERSION 8u181

# VSCode
WORKDIR /tmp
COPY vscode/code-1.35.1-1560350390.el7.x86_64.rpm ./
#RUN yum -y localinstall ./code-1.35.1-1560350390.el7.x86_64.rpm

EXPOSE 22
CMD /sbin/init
