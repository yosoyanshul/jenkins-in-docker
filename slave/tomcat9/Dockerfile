FROM tomcat:9.0.73-jdk11-corretto 

#RUN apt-get update && apt-get -y upgrade

WORKDIR /usr/local/tomcat

User root

RUN mv /usr/local/tomcat/webapps /usr/local/tomcat/webapps2
RUN mv /usr/local/tomcat/webapps.dist/ webapps

#COPY server.xml /usr/local/tomcat/conf/
COPY tomcat-users.xml /usr/local/tomcat/conf/
COPY context.xml /usr/local/tomcat/webapps/manager/META-INF/
COPY context.xml /usr/local/tomcat/webapps/host-manager/META-INF/
#COPY catalina.sh /usr/local/tomcat/bin/

EXPOSE 8080

CMD ["catalina.sh", "run"]
