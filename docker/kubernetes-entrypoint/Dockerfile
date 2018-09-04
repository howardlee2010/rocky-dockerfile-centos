FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="kubernetes-entrypoint" build-date="20180904"




RUN curl -Lo /usr/local/bin/kubernetes-entrypoint https://github.com/stackanetes/kubernetes-entrypoint/releases/download/v0.1.1/kubernetes-entrypoint \
    && chmod 755 /usr/local/bin/kubernetes-entrypoint




CMD /usr/local/bin/kubernetes-entrypoint