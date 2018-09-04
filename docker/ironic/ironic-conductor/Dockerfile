FROM kolla/centos-source-ironic-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ironic-conductor" build-date="20180904"






    
        
    



RUN pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt -r /ironic/driver-requirements.txt


RUN yum -y install dosfstools e2fsprogs fuse gdisk ipmitool parted psmisc qemu-img-ev shellinabox util-linux xfsprogs && yum clean all && rm -rf /var/cache/yum

COPY extend_start.sh /usr/local/bin/kolla_ironic_extend_start
COPY iscsi_tcp_sudoers /etc/sudoers.d/kolla_iscsi_tcp_sudoers
RUN chmod 755 /usr/local/bin/kolla_ironic_extend_start \
    && chmod 440 /etc/sudoers.d/kolla_iscsi_tcp_sudoers




USER ironic