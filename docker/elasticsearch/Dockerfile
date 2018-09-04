FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="elasticsearch" build-date="20180904"







RUN usermod --append --home /usr/share/elasticsearch --groups kolla elasticsearch \
    && chsh --shell /bin/bash elasticsearch \
    && mkdir -p /usr/share/elasticsearch \
    && chown -R 42412:42412 /usr/share/elasticsearch



    

ENV JAVA_HOME /usr/lib/jvm/jre-1.8.0-openjdk/



ENV ES_SKIP_SET_KERNEL_PARAMETERS true

RUN yum -y install elasticsearch java-1.8.0-openjdk-headless && yum clean all && rm -rf /var/cache/yum
COPY extend_start.sh /usr/local/bin/kolla_extend_start

# NOTE: By default the shell of the elasticsearch user is /bin/false. We have to
# change the shell to /bin/bash to be able to run elasticsearch as a non-root user.
#
# https://discuss.elastic.co/t/running-as-non-root-user-service-wrapper-has-changed/7863

RUN chmod 755 /usr/local/bin/kolla_extend_start




USER elasticsearch