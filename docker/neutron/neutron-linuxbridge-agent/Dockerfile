FROM kolla/centos-source-neutron-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="neutron-linuxbridge-agent" build-date="20180904"







    



RUN yum -y install bridge-utils ebtables && yum clean all && rm -rf /var/cache/yum




USER neutron