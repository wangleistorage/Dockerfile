FROM dockerimage.xkeshi.so/centos7

ENV JAVA_HOME /usr/local/jdk
ENV JAVA_BIN $JAVA_HOME/bin
ENV CLASSPATH $JAVA_HOME/lib/dt.jar,$JAVA_HOME/lib/tools.jar
ENV PATH $PATH:$JAVA_HOME:$JAVA_BIN:$CLASSPATH

COPY jdk $JAVA_HOME
COPY tomcat /usr/local/tomcat

EXPOSE 8080

CMD ["/usr/local/tomcat/bin/catalina.sh", "start"]
