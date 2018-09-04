FROM kolla/centos-source-neutron-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="neutron-metadata-agent-ovn" build-date="20180904"







ADD plugins-archive /

    

RUN if [ "$(ls /plugins)" ]; then \
        pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /plugins/*; \
    fi






USER neutron