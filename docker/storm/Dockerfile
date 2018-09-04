FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="storm" build-date="20180904"







RUN usermod --append --home /opt/storm --groups kolla storm \
    && mkdir -p /opt/storm \
    && chown -R 42479:42479 /opt/storm



    


RUN yum -y install java-1.8.0-openjdk-headless && yum clean all && rm -rf /var/cache/yum


ENV storm_version=1.1.2
ENV storm_url=http://www.mirrorservice.org/sites/ftp.apache.org/storm/apache-storm-${storm_version}/apache-storm-${storm_version}.tar.gz
ENV storm_pkg_sha512sum=4ec7554d4e242c5cfa3b010f63b2ed65866d0768bfa04c7ae87004d21994041ef25b198a236a87f14ac3b36b698f117338080d9b7d9c0f561b7de256bf2e10d2



RUN curl -sSL -o /tmp/storm.tgz ${storm_url} \
    && echo "${storm_pkg_sha512sum} /tmp/storm.tgz" | sha512sum -c \
    && tar --strip 1 -xvf /tmp/storm.tgz -C /opt/storm \
    && rm -f /tmp/storm.tgz



COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start




USER storm