# Image for Oxygen Web Author server
#
# http://mirror.oxygenxml.com/InstData/WebAuthor/war/oxygenxml-web-author.war
FROM tomcat:9-alpine
MAINTAINER Eliot Kimber <ekimber@contrext.com>

RUN apk add --update curl unzip

# NOTE: current directory is /usr/local/tomcat

ADD oxygenxml-web-author.war /usr/local/tomcat/webapps/
RUN unzip webapps/oxygenxml-web-author.war -d /usr/local/tomcat/webapps/oxygenxml-web-author
RUN rm /usr/local/tomcat/webapps/oxygenxml-web-author.war
ADD settings.xml /usr/local/tomcat/conf/
ADD tomcat-users.xml /usr/local/tomcat/conf/
ADD license.properties /usr/local/tomcat/webapps/oxygenxml-web-author/WEB-INF/
RUN ls /usr/local/tomcat/webapps/oxygenxml-web-author/WEB-INF/

#
# End of Dockerfile
#