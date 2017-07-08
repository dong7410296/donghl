FROM openjdk:8-jre

RUN mkdir /soft

WORKDIR /soft

RUN apt-get update

RUN apt-get install -y vim

RUN wget http://mirrors.hust.edu.cn/apache/tomcat/tomcat-8/v8.5.16/bin/apache-tomcat-8.5.16.tar.gz
RUN tar zxvf apache-tomcat-8.5.16.tar.gz
RUN mv apache-tomcat-8.5.16 tomcat
ENV TOMCAT_HOME /soft/tomcat
ENV PATH $TOMCAT_HOME/bin:$PATH
RUN rm -rf $TOMCAT_HOME/webapps/ROOT
RUN sed -i '1i\JAVA_OPTS="-Djava.security.egd=file:/dev/./urandom"' $TOMCAT_HOME/bin/catalina.sh

COPY /code/sunday/sunday/target/sunday.war $TOMCAT_HOME/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]