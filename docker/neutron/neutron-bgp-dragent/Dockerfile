FROM kolla/centos-source-neutron-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="neutron-bgp-dragent" build-date="20180904"







ADD neutron-bgp-dragent-archive /neutron-bgp-dragent-source

    

RUN ln -s neutron-bgp-dragent-source/* neutron_dynamic_routing \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /neutron_dynamic_routing






USER neutron