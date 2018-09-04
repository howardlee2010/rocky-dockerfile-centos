FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="kafka" build-date="20180904"







RUN usermod --append --home /opt/kafka --groups kolla kafka \
    && mkdir -p /opt/kafka \
    && chown -R 42423:42423 /opt/kafka



    


RUN yum -y install java-1.8.0-openjdk-headless && yum clean all && rm -rf /var/cache/yum


ENV kafka_version=1.0.1
ENV kafka_scala_version=2.12
ENV kafka_url=http://apache.osuosl.org/kafka/${kafka_version}/kafka_${kafka_scala_version}-${kafka_version}.tgz
ENV kafka_pkg_sha512sum=935c0df1cf742405c40d9248cfdd1578038b595b59ec5a350543a7fe67b6be26ff6c4426f7c0c072ff4aa006b701502a55fcf7e2ced1fdc64330e3383035078c



RUN curl -sSL -o /tmp/kafka.tgz ${kafka_url} \
    && echo "${kafka_pkg_sha512sum} /tmp/kafka.tgz" | sha512sum -c \
    && tar --strip 1 -xvf /tmp/kafka.tgz -C /opt/kafka \
    && rm -f /tmp/kafka.tgz


COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start




USER kafka