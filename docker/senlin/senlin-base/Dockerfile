FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="senlin-base" build-date="20180904"








RUN usermod --append --home /var/lib/senlin --groups kolla senlin \
    && mkdir -p /var/lib/senlin \
    && chown -R 42443:42443 /var/lib/senlin




ADD senlin-base-archive /senlin-base-source



RUN ln -s senlin-base-source/* senlin \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /senlin \
    && mkdir -p /etc/senlin \
    && cp -r /senlin/etc/senlin/* /etc/senlin \
    && chown -R senlin: /etc/senlin



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_senlin_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_senlin_extend_start

