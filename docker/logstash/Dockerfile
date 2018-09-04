FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="logstash" build-date="20180904"







RUN usermod --append --home /usr/share/logstash --groups kolla logstash \
    && chsh --shell /bin/bash logstash \
    && mkdir -p /usr/share/logstash \
    && chown -R 42478:42478 /usr/share/logstash



    

ENV JAVA_HOME /usr/lib/jvm/jre-1.8.0-openjdk/



RUN yum -y install logstash java-1.8.0-openjdk-headless && yum clean all && rm -rf /var/cache/yum
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN chmod 755 /usr/local/bin/kolla_extend_start




USER logstash