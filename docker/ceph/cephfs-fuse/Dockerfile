FROM kolla/centos-source-ceph-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="cephfs-fuse" build-date="20180904"






# Clear any customisation by Kolla to entrypoint & command
ENTRYPOINT ["/usr/bin/ceph-fuse"]
CMD []