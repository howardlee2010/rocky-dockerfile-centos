FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ironic-base" build-date="20180904"








RUN usermod --append --home /var/lib/ironic --groups kolla ironic \
    && mkdir -p /var/lib/ironic \
    && chown -R 42422:42422 /var/lib/ironic




ADD ironic-base-archive /ironic-base-source



RUN ln -s ironic-base-source/* ironic \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /ironic \
    && mkdir -p /etc/ironic \
    && cp -r /ironic/etc/ironic/* /etc/ironic/ \
    && chown -R ironic: /etc/ironic \
    && sed -i 's|^exec_dirs.*|exec_dirs=/var/lib/kolla/venv/bin,/sbin,/usr/sbin,/bin,/usr/bin,/usr/local/bin,/usr/local/sbin|g' /etc/ironic/rootwrap.conf

ADD ironic_sudoers /etc/sudoers.d/kolla_ironic_sudoers
RUN chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/kolla_ironic_sudoers



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_ironic_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_ironic_extend_start \
    && chown -R ironic: /etc/ironic

