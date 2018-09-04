FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="rabbitmq" build-date="20180904"








RUN usermod --append --home /var/lib/rabbitmq --groups kolla rabbitmq \
    && mkdir -p /var/lib/rabbitmq \
    && chown -R 42439:42439 /var/lib/rabbitmq




    



RUN yum -y install erlang-hipe hostname rabbitmq-server && yum clean all && rm -rf /var/cache/yum





RUN rm -rf /var/lib/rabbitmq/* \
    && ln -s /usr/lib/rabbitmq/lib/rabbitmq_server-3.6.* /usr/lib/rabbitmq/lib/rabbitmq_server-3.6 \
    && curl -o /usr/lib/rabbitmq/lib/rabbitmq_server-3.6/plugins/rabbitmq_clusterer-3.6.x-667f92b0.ez http://www.rabbitmq.com/community-plugins/v3.6.x/rabbitmq_clusterer-3.6.x-667f92b0.ez \
    && /usr/lib/rabbitmq/bin/rabbitmq-plugins enable --offline \
       rabbitmq_management \
       rabbitmq_clusterer



COPY extend_start.sh /usr/local/bin/kolla_extend_start
COPY rabbitmq_get_gospel_node.py /usr/local/bin/rabbitmq_get_gospel_node
RUN chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/rabbitmq_get_gospel_node




USER rabbitmq