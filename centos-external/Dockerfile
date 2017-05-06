
FROM centos:latest

MAINTAINER zhuhh (jackjboss@gmail.com)

#centos镜像默认没有server服务，所以需要安装 /sbin/service
RUN yum -y install initscripts && yum clean all

#RUN yum -y install curl

#Install JDK 7  
RUN cd /tmp &&  curl -L 'http://download.oracle.com/otn-pub/java/jdk/7u65-b17/jdk-7u65-linux-x64.tar.gz' -H 'Cookie: oraclelicense=accept-securebackup-cookie; gpw_e24=Dockerfile' | tar -xz
RUN mkdir -p /usr/lib/jvm
RUN mv /tmp/jdk1.7.0_65/ /usr/lib/jvm/java-7-oracle/

RUN update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-7-oracle/bin/java 300
RUN update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/java-7-oracle/bin/javac 300

ENV JAVA_HOME /usr/lib/jvm/java-7-oracle/ 

#Install tomcat7  
RUN cd /tmp && curl -L 'http://archive.apache.org/dist/tomcat/tomcat-7/v7.0.8/bin/apache-tomcat-7.0.8.tar.gz' | tar -xz
RUN mv /tmp/apache-tomcat-7.0.8/ /opt/tomcat7/

ENV CATALINA_HOME /opt/tomcat7
ENV PATH $PATH:$CATALINA_HOME/bin

ADD cdn-api.war /opt/tomcat7/webapps/cdn-api.war

# Expose ports.
EXPOSE 8080

CMD ["/opt/tomcat7/bin/catalina.sh","run"]
