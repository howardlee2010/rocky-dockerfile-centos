FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="tempest" build-date="20180904"








RUN usermod --append --home /var/lib/tempest --groups kolla tempest \
    && mkdir -p /var/lib/tempest \
    && chown -R 42480:42480 /var/lib/tempest




ADD tempest-archive /tempest-source
ADD plugins-archive /





# NOTE(Jeffrey4l): remove the tempest version constraint in the
# upper-constrains.txt file. Otherwise, it will be failed.
RUN ln -s tempest-source/* tempest \
    && sed -i 's/^tempest===.*$//' requirements/upper-constraints.txt \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /tempest \
    && if [ "$(ls /plugins)" ]; then \
        pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /plugins/*; \
       fi \
    && mkdir -p /etc/tempest /var/log/tempest /etc/tempest/tempest_lock



WORKDIR /tempest

COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start




USER tempest