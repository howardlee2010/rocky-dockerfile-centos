FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="murano-base" build-date="20180904"








RUN usermod --append --home /var/lib/murano --groups kolla murano \
    && mkdir -p /var/lib/murano \
    && chown -R 42433:42433 /var/lib/murano




ADD murano-base-archive /murano-base-source



RUN ln -s murano-base-source/* murano \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /murano \
    && mkdir -p /etc/murano \
    && cp -r /murano/etc/murano/* /etc/murano/ \
    && chown -R murano: /etc/murano \
    && cd murano/meta/io.murano \
    && zip -r /io.murano.zip * \
    && cd /murano/meta/io.murano.applications \
    && zip -r /io.murano.applications.zip *



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_murano_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_murano_extend_start

