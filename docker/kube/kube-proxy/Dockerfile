FROM kolla/centos-source-kube-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="kube-proxy" build-date="20180904"

ENV KUBERNETES_COMPONENT=kube-proxy




RUN true \
    && curl -L ${KUBERNETES_DOWNLOAD_ROOT}/${KUBERNETES_COMPONENT} -o /usr/bin/${KUBERNETES_COMPONENT} \
    && chmod +x /usr/bin/${KUBERNETES_COMPONENT}


# Clear any customisation by Kolla to entrypoint & command
ENTRYPOINT []
CMD []


