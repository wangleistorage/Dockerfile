FROM centos7:latest

RUN yum -y install openssh-clients openssh-server supervisor ansible

RUN mkdir -p /root/.ssh

RUN ssh-keygen -q -f /etc/ssh/ssh_host_key -N '' -t rsa1
RUN ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa
RUN ssh-keygen -f /etc/ssh/ssh_host_dsa_key -N '' -t dsa

RUN echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDihpDzUoq3xIPOg+2GZfLpCIh+JCVXeYOTFsTCx+qh0Q+6kJ8BacjEzLvIDkuQXDi9r5uFxrAi5Ao6ZPPQgNyk4M2SCDrMWH/+NNxSz4QjRLrHh55l99A7D1IEgVTiBDGo23Xlv9P5qJSEyWE65JKI3hu86v7YR/cNLeszjaZr0gbmLQ9ID4RNSKbj6ez4RotEgq/QAYJNA5VBJ/7oBpqW7KRLIBjHF8pAizAlCndp87gMbXqaRAMDdNkS00mJVFGSdbixClrSnMzHoMnwVIANR6vnMMhQIfzuMEyYnxddDn1lJdaVg49hNOayv0cJdubMDQVdG4BS8w5Z4Ju8RKj3" >> /root/.ssh/authorized_keys

COPY ansible.cfg /etc/ansible/ansible.cfg
COPY supervisor.conf /etc/supervisord.conf

EXPOSE 22

CMD ["/usr/bin/supervisord"]
