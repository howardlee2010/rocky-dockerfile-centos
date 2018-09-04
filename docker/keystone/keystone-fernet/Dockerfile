FROM kolla/centos-source-keystone-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="keystone-fernet" build-date="20180904"






    

RUN yum -y install cronie openssh-clients rsync && yum clean all && rm -rf /var/cache/yum

COPY fetch_fernet_tokens.py /usr/bin/
COPY keystone_bootstrap.sh /usr/local/bin/kolla_keystone_bootstrap
COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_keystone_bootstrap /usr/bin/fetch_fernet_tokens.py


