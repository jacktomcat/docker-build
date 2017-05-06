
FROM centos:latest

MAINTAINER zhuhh (jackjboss@gmail.com)

#centos镜像默认没有server服务，所以需要安装 /sbin/service
RUN yum -y install net-tools
RUN yum -y install initscripts && yum clean all

ADD jdk1.7.0_80 /opt/jdk1.7.0_80
ADD tomcat-7.0.73 /opt/tomcat-7.0.73
ADD java.sh /etc/profile.d/java.sh
ADD cdn-api.war /opt/tomcat-7.0.73/webapps/cdn-api.war

ENV JAVA_HOME /opt/jdk1.7.0_80
ENV CATALINA_HOME /opt/tomcat-7.0.73
ENV PATH $PATH:$CATALINA_HOME/bin

RUN . /etc/profile.d/java.sh

EXPOSE 8080

CMD ["/opt/tomcat-7.0.73/bin/catalina.sh","run"]

#ENTRYPOINT /opt/tomcat-7.0.73/bin/startup.sh

