FROM kolla/centos-source-rsyslog-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="rsyslog" build-date="20180904"






    


RUN yum -y install rsyslog-elasticsearch rsyslog-gnutls rsyslog-mmjsonparse rsyslog-mmnormalize && yum clean all && rm -rf /var/cache/yum


