FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="freezer-base" build-date="20180904"








RUN usermod --append --home /var/lib/freezer --groups kolla freezer \
    && mkdir -p /var/lib/freezer \
    && chown -R 42414:42414 /var/lib/freezer



    
RUN yum -y install trickle && yum clean all && rm -rf /var/cache/yum

ADD freezer-base-archive /freezer-base-source



RUN ln -s freezer-base-source/* freezer \
    && mkdir -p /etc/freezer \
    && chown -R freezer: /etc/freezer \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /freezer \
    && cp -r /freezer/etc/* /etc/freezer



COPY freezer_sudoers /etc/sudoers.d/kolla_freezer_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN chmod 750 /etc/sudoers.d \
    && chmod 640 /etc/sudoers.d/kolla_freezer_sudoers \
    && touch /usr/local/bin/kolla_freezer_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_freezer_extend_start

