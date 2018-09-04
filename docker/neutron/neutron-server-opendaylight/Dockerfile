FROM kolla/centos-source-neutron-server:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="neutron-server-opendaylight" build-date="20180904"

USER root







    

ADD plugins-archive /



RUN if [ "$(ls /plugins)" ]; then \
        pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /plugins/*; \
    fi






USER neutron