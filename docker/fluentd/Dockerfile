FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="fluentd" build-date="20180904"







    


RUN usermod --append --home /var/lib/fluentd --groups kolla fluentd \
    && usermod --append --groups mysql fluentd \
    && mkdir -p /var/lib/fluentd \
    && chown -R 42474:42474 /var/lib/fluentd

# TODO:remove hostname package as it should be installed by the
# fluentd dependencies.
# hostname package is installed by default on CentOS/RHEL but not on
# oraclelinux.

    



RUN yum -y install fluentd hostname rubygem-fluent-plugin-elasticsearch rubygem-fluent-plugin-grok-parser rubygem-fluent-plugin-kubernetes_metadata_filter rubygem-fluent-plugin-rewrite-tag-filter rubygem-fluent-plugin-secure-forward && yum clean all && rm -rf /var/cache/yum

# Distro specific files and operations

COPY rpm_fluentd_sudoers /etc/sudoers.d/kolla_fluentd_sudoers
RUN chmod 440 /etc/sudoers.d/kolla_fluentd_sudoers \
    && mkdir -p /var/run/fluentd \
    && chown -R fluentd: /etc/fluentd /var/run/fluentd



COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start













USER fluentd
