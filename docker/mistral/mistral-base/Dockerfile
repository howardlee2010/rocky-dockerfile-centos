FROM kolla/centos-source-openstack-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="mistral-base" build-date="20180904"








RUN usermod --append --home /var/lib/mistral --groups kolla mistral \
    && mkdir -p /var/lib/mistral \
    && chown -R 42430:42430 /var/lib/mistral




ADD mistral-base-archive /mistral-base-source
ADD plugins-archive /





RUN ln -s mistral-base-source/* mistral \
    && pip --no-cache-dir install --upgrade /mistral redis \
    && mkdir -p /etc/mistral \
    && cp -r /mistral/etc/* /etc/mistral/ \
    && chown -R mistral: /etc/mistral \
    && if [ "$(ls /plugins)" ]; then \
        pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /plugins/*; \
    fi


COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_mistral_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_mistral_extend_start