FROM kolla/centos-source-swift-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="swift-proxy-server" build-date="20180904"









RUN pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt ceilometermiddleware



COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start




USER swift