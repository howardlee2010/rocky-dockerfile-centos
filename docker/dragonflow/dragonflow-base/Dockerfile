FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="dragonflow-base" build-date="20180904"








RUN usermod --append --home /var/lib/dragonflow --groups kolla dragonflow \
    && mkdir -p /var/lib/dragonflow \
    && chown -R 42464:42464 /var/lib/dragonflow





    



RUN yum -y install zeromq-devel && yum clean all && rm -rf /var/cache/yum



ADD dragonflow-base-archive /dragonflow-base-source
RUN ln -s dragonflow-base-source/* dragonflow \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /dragonflow \
    && mkdir -p /etc/dragonflow \
    && cp -r /dragonflow/etc/* /etc/dragonflow/ \
    && chown -R dragonflow: /etc/dragonflow



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_dragonflow_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_dragonflow_extend_start

