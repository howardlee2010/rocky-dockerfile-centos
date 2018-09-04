FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="tacker-base" build-date="20180904"








RUN usermod --append --home /var/lib/tacker --groups kolla tacker \
    && mkdir -p /var/lib/tacker \
    && chown -R 42446:42446 /var/lib/tacker




ADD tacker-base-archive /tacker-base-source
ADD plugins-archive /





RUN ln -s tacker-base-source/* tacker \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /tacker \
    && mkdir -p /etc/tacker \
    && cp -r /tacker/etc/tacker/* /etc/tacker \
    && chown -R tacker: /etc/tacker \
    && if [ "$(ls /plugins)" ]; then \
        pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /plugins/*; \
    fi



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_tacker_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_tacker_extend_start

