FROM openeuler/openeuler:24.03

RUN yum -y install \
    gcc \
    gcc-c++ \
    ccache \
    flex \
    git \
    bison \
    cmake \
    curl \
    findutils \
    libpcap-devel \
    make \
    openssl \
    openssl-devel \
    python3 \
    python3-devel \
    sqlite \
    swig \
    which \
    zlib-devel \
  && yum clean all && rm -rf /var/cache/yum

RUN pip3 install websockets junit2html
