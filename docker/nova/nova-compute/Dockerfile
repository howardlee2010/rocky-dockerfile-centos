FROM kolla/centos-source-nova-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="nova-compute" build-date="20180904"






    

        

    

RUN yum -y install ceph-common device-mapper-multipath dosfstools e2fsprogs genisoimage iscsi-initiator-utils libvirt-python libosinfo nfs-utils openvswitch parted python-libguestfs python-rtslib qemu-img-ev sysfsutils targetcli && yum clean all && rm -rf /var/cache/yum





ADD plugins-archive /
RUN pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt oslo-vmware \
    && if [ "$(ls /plugins)" ]; then \
           pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /plugins/*; \
       fi



COPY extend_start.sh /usr/local/bin/kolla_nova_extend_start
RUN chmod 755 /usr/local/bin/kolla_nova_extend_start \
    && rm -f /etc/machine-id




USER nova