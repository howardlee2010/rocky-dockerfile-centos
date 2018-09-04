FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="zookeeper" build-date="20180904"







RUN usermod --append --home /opt/zookeeper --groups kolla zookeeper \
    && mkdir -p /opt/zookeeper \
    && chown -R 42453:42453 /opt/zookeeper



    


RUN yum -y install java-1.8.0-openjdk-headless && yum clean all && rm -rf /var/cache/yum


ENV zookeeper_version=3.4.10
ENV zookeeper_url=http://apache.mirror.anlx.net/zookeeper/zookeeper-${zookeeper_version}/zookeeper-${zookeeper_version}.tar.gz
ENV zookeeper_pkg_sha1sum=eb2145498c5f7a0d23650d3e0102318363206fba



RUN curl -sSL -o /tmp/zookeeper.tar.gz ${zookeeper_url} \
    && echo "${zookeeper_pkg_sha1sum} /tmp/zookeeper.tar.gz" | sha1sum -c \
    && tar --strip 1 -xvf /tmp/zookeeper.tar.gz -C /opt/zookeeper \
    && rm -f /tmp/zookeeper.tar.gz


COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start




USER zookeeper