FROM centos:7

# Centos 7 EOL is 2024-06-30, 
# We need to use the vault repo to install the required packages.
RUN sed -i \
    -e 's/^mirrorlist/#mirrorlist/' \
    -e 's/^#baseurl/baseurl/' \
    -e 's/mirror\.centos\.org/vault.centos.org/' \
    /etc/yum.repos.d/*.repo

RUN yum -y install \
    epel-release \
    centos-release-scl \
  && yum clean all && rm -rf /var/cache/yum

RUN sed -i \
    -e 's/^mirrorlist/#mirrorlist/' \
    -e 's/^#baseurl/baseurl/' \
    -e 's/^# baseurl/baseurl/' \
    -e 's/mirror\.centos\.org/vault.centos.org/' \
    /etc/yum.repos.d/CentOS-SCLo-scl*.repo

RUN yum -y install \
    flex \
    bison \
    cmake3 \
    curl \
    ccache \
    git \
    findutils \
    libpcap-devel \
    make \
    openssl \
    openssl-devel \
    rh-python38 \
    rh-python38-devel \
    rh-python38-python-devel \
    rh-python38-pip \
    sqlite \
    swig \
    which \
    zlib-devel \
    devtoolset-11 \
    rh-git227 \
  && yum clean all && rm -rf /var/cache/yum

RUN pip3 install websockets junit2html

RUN echo 'unset BASH_ENV PROMPT_COMMAND ENV' > /usr/bin/zeek-ci-env && \
    echo 'source /opt/rh/devtoolset-11/enable' >> /usr/bin/zeek-ci-env && \
    echo 'source /opt/rh/rh-python38/enable' >> /usr/bin/zeek-ci-env && \
    echo 'source /opt/rh/rh-git227/enable' >> /usr/bin/zeek-ci-env

ENV BASH_ENV="/usr/bin/zeek-ci-env" \
    ENV="/usr/bin/zeek-ci-env" \
    PROMPT_COMMAND=". /usr/bin/zeek-ci-env"
