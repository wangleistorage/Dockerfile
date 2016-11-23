From centos7:latest

# yum install depandent
RUN yum -y install openssh-server supervisor ansible

# ssh config
RUN mkdir -p /root/.ssh
RUN ssh-keygen -q -f /etc/ssh/ssh_host_key -N '' -t rsa1
RUN ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa
RUN ssh-keygen -f /etc/ssh/ssh_host_dsa_key -N '' -t dsa
RUN echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDihpDzUoq3xIPOg+2GZfLpCIh+JCVXeYOTFsTCx+qh0Q+6kJ8BacjEzLvIDkuQXDi9r5uFxrAi5Ao6ZPPQgNyk4M2SCDrMWH/+NNxSz4QjRLrHh55l99A7D1IEgVTiBDGo23Xlv9P5qJSEyWE65JKI3hu86v7YR/cNLeszjaZr0gbmLQ9ID4RNSKbj6ez4RotEgq/QAYJNA5VBJ/7oBpqW7KRLIBjHF8pAizAlCndp87gMbXqaRAMDdNkS00mJVFGSdbixClrSnMzHoMnwVIANR6vnMMhQIfzuMEyYnxddDn1lJdaVg49hNOayv0cJdubMDQVdG4BS8w5Z4Ju8RKj3" >> /root/.ssh/authorized_keys

# env variable config
ENV JAVA_HOME /usr/local/jdk
ENV JAVA_BIN $JAVA_HOME/bin
ENV CLASSPATH $JAVA_HOME/lib/dt.jar,$JAVA_HOME/lib/tools.jar
ENV JENKINS_HOME /data/jenkins
ENV M2_HOME /opt/apache-maven
ENV PATH $PATH:$JAVA_HOME:$JAVA_BIN:$CLASSPATH:$M2_HOME/bin

# supervisor jenkins jdk maven config
COPY supervisor.conf /etc/supervisord.conf
COPY jdk $JAVA_HOME
COPY jenkins /usr/local/jenkins
COPY jenkins.war /usr/local/jenkins/webapps/jenkins.war
COPY apache-maven /opt/apache-maven

# map port
EXPOSE 22
EXPOSE 8080

# cmd
CMD ["/usr/bin/supervisord"]
