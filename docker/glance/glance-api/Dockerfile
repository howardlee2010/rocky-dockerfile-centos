FROM kolla/centos-source-glance-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="glance-api" build-date="20180904"






    


RUN yum -y install qemu-img-ev && yum clean all && rm -rf /var/cache/yum

COPY extend_start.sh /usr/local/bin/kolla_glance_extend_start
RUN chmod 755 /usr/local/bin/kolla_glance_extend_start




USER glance