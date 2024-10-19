FROM hxsoong/kylin:v10-sp3

COPY ./CentOS-SCLo-scl-rh.repo /etc/yum.repos.d/

RUN yum -y install \
    flex \
    bison \
    cmake3 \
    curl \
    findutils \
    libpcap-devel \
    make \
    openssl \
    openssl-devel \
    python3 \
    python3-devel \
    python3-pip \
    sqlite \
    swig \
    which \
    zlib-devel \
    devtoolset-11-gcc-c++ \
    git \
  && yum clean all && rm -rf /var/cache/yum

RUN pip3 install websockets junit2html

RUN echo 'unset BASH_ENV PROMPT_COMMAND ENV' > /usr/bin/zeek-ci-env && \
    echo 'source /opt/rh/devtoolset-11/enable' >> /usr/bin/zeek-ci-env

ENV BASH_ENV="/usr/bin/zeek-ci-env" \
    ENV="/usr/bin/zeek-ci-env" \
    PROMPT_COMMAND=". /usr/bin/zeek-ci-env"
