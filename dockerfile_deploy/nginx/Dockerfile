FROM centos7:latest

ENV nginx_path /usr/local/nginx

RUN yum -y install supervisor
RUN mkdir -p /root/.ssh
RUN mkdir -p $nginx_path/auth
RUN mkdir -p $nginx_path/conf/vhost
RUN echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDihpDzUoq3xIPOg+2GZfLpCIh+JCVXeYOTFsTCx+qh0Q+6kJ8BacjEzLvIDkuQXDi9r5uFxrAi5Ao6ZPPQgNyk4M2SCDrMWH/+NNxSz4QjRLrHh55l99A7D1IEgVTiBDGo23Xlv9P5qJSEyWE65JKI3hu86v7YR/cNLeszjaZr0gbmLQ9ID4RNSKbj6ez4RotEgq/QAYJNA5VBJ/7oBpqW7KRLIBjHF8pAizAlCndp87gMbXqaRAMDdNkS00mJVFGSdbixClrSnMzHoMnwVIANR6vnMMhQIfzuMEyYnxddDn1lJdaVg49hNOayv0cJdubMDQVdG4BS8w5Z4Ju8RKj3" >> /root/.ssh/authorized_keys

COPY nginx $nginx_path
COPY certs $nginx_path/certs
COPY docker.wanglei.net.conf $nginx_path/conf/vhost/docker.wanglei.net.conf 
COPY nginx.conf $nginx_path/conf/nginx.conf
COPY htpasswd.txt $nginx_path/auth/htpasswd.txt
COPY supervisor.conf /etc/supervisord.conf

EXPOSE 22 80 443

CMD ["/usr/bin/supervisord"]

