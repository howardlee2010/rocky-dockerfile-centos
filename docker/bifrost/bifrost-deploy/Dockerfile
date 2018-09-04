FROM kolla/centos-source-bifrost-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="bifrost-deploy" build-date="20180904"



ENV container docker





RUN rm -f $(find /lib/systemd/system/sysinit.target.wants/ ! -name systemd-tmpfiles-setup.service -type l); \
    rm -f /lib/systemd/system/multi-user.target.wants/*; \
    rm -f /etc/systemd/system/*.wants/*; \
    rm -f /lib/systemd/system/local-fs.target.wants/*; \
    rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
    rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
    rm -f /lib/systemd/system/basic.target.wants/*; \
    rm -f /lib/systemd/system/anaconda.target.wants/*;





RUN yum -y install e2fsprogs && yum clean all && rm -rf /var/cache/yum

CMD [ "/sbin/init" ]


