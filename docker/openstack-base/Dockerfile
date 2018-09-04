FROM kolla/centos-source-base:7.0.0
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="openstack-base" build-date="20180904"






    
        

    

RUN yum -y install gcc gcc-c++ git iproute libffi-devel libxml2-devel libxslt-devel libyaml-devel mariadb-devel openldap-devel openssl openssl-devel postgresql postgresql-devel python-devel sqlite-devel zip && yum clean all && rm -rf /var/cache/yum


RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py \
    && python get-pip.py \
    && rm get-pip.py




ADD openstack-base-archive /openstack-base-source
RUN ln -s openstack-base-source/* /requirements \
    && mkdir -p /var/lib/kolla \
    && pip --no-cache-dir install --upgrade virtualenv \
    && virtualenv --system-site-packages /var/lib/kolla/venv

ENV PATH /var/lib/kolla/venv/bin:$PATH

RUN pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt Babel Mako MarkupSafe Paste PasteDeploy PyYAML Routes SQLAlchemy Tempita WebOb alembic amqp anyjson aodhclient appdirs cachetools cliff cmd2 cryptography contextlib2 debtcollector decorator elasticsearch enum34 eventlet fasteners funcsigs functools32 futures futurist gnocchiclient greenlet iso8601 jinja2 jsonpatch jsonpointer jsonschema keystoneauth1 keystonemiddleware kombu monotonic msgpack-python MySQL-python netaddr netifaces os-client-config oslo.concurrency oslo.config oslo.context oslo.db oslo.i18n oslo.log oslo.messaging oslo.middleware oslo.policy oslo.serialization oslo.service oslo.utils oslo.vmware osprofiler pbr pika pika-pool prettytable pycadf pyinotify pymysql pyngus pyparsing python-barbicanclient python-cinderclient python-cloudkittyclient python-congressclient python-dateutil python-designateclient python-editor python-glanceclient python-heatclient python-ironicclient python-keystoneclient python-magnumclient python-manilaclient python-memcached python-mistralclient python-muranoclient python-neutronclient python-novaclient python-openstackclient python-qpid-proton python-saharaclient python-swiftclient python-troveclient python-vitrageclient python-zaqarclient pytz repoze.lru requests requestsexceptions retrying simplejson six sqlalchemy-migrate sqlparse stevedore tooz[consul,etcd,etcd3,etcd3gw,zake,redis,postgresql,mysql,zookeeper,memcached,ipc] unicodecsv warlock wrapt



