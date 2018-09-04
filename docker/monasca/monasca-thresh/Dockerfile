FROM kolla/centos-source-storm:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="monasca-thresh" build-date="20180904"

USER root








    

ENV JAVA_HOME /usr/lib/jvm/jre-1.8.0-openjdk/



RUN yum -y install maven && yum clean all && rm -rf /var/cache/yum

ADD monasca-thresh-archive /monasca-thresh-source
ADD additions/monasca-common* /monasca-common-source





# FIXME(dszumski): Remove this when the following bug is fixed:
# https://bugs.launchpad.net/ubuntu/+source/ca-certificates-java/+bug/1770553


RUN cd /monasca-common-source/java \
    && mvn clean install -DskipTests \
    && cd /monasca-thresh-source/monasca-thresh-*/thresh \
    && mvn clean package -DskipTests







USER monasca