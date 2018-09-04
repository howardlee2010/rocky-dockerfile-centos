FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="helm-repository" build-date="20180904"


ENV helm_version=2.3.0 \
    helm_port=8879 \
    helm_address=0.0.0.0









    


RUN yum -y install git jq python2-pip && yum clean all && rm -rf /var/cache/yum


RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py \
    && python get-pip.py \
    && rm get-pip.py




RUN pip --no-cache-dir install --upgrade pyyaml


ENV helm_arch=amd64



RUN curl -Lo /tmp/helm-v${helm_version}-linux-${helm_arch}.tar.gz  http://storage.googleapis.com/kubernetes-helm/helm-v${helm_version}-linux-${helm_arch}.tar.gz \
    && sudo tar --strip-components 1 -C /usr/bin linux-${helm_arch}/helm -zxvf /tmp/helm-v${helm_version}-linux-${helm_arch}.tar.gz \
    && sudo chmod 755 /usr/bin/helm \
    && rm /tmp/helm-v${helm_version}-linux-${helm_arch}.tar.gz


RUN useradd --user-group --create-home --home-dir /home/helm helm \
    && sudo mkdir /helm-repo \
    && sudo chmod 755 /helm-repo \
    && sudo chown -R helm: /helm-repo/

USER helm

RUN helm init --client-only

CMD helm serve --address $helm_address:$helm_port --repo-path /helm-repo


