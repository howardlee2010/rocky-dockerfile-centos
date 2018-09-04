FROM kolla/centos-source-designate-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="designate-worker" build-date="20180904"





# The bind9 package here is only to provide the rndc binary.

    
       
    

RUN yum -y install bind && yum clean all && rm -rf /var/cache/yum




USER designate