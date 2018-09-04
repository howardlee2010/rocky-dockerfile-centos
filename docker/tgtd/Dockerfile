FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="tgtd" build-date="20180904"






    

RUN yum -y install scsi-target-utils && yum clean all && rm -rf /var/cache/yum
RUN sed -i '1 i include /var/lib/cinder/volumes/*' /etc/tgt/tgtd.conf




