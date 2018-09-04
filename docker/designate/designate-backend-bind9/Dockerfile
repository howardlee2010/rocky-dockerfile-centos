FROM kolla/centos-source-designate-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="designate-backend-bind9" build-date="20180904"






   

RUN yum -y install bind && yum clean all && rm -rf /var/cache/yum





RUN mkdir -p /var/lib/kolla/ /var/lib/named/ /run/named \
     && chown -R root: /var/lib/named /run/named \
     && chmod 755 /run/named \


