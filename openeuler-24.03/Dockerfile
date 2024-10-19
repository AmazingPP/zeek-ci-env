FROM openeuler/openeuler:24.03

RUN sed -i \
    -e 's|repo.openeuler.org|mirrors.tuna.tsinghua.edu.cn/openeuler|g' \
    -e 's|^metalink|#metalink|g' \
    /etc/yum.repos.d/openEuler.repo

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
    libasan \
    libtsan \
    libubsan \
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
  && yum clean all && rm -rf /var/cache/yum

RUN pip3 install websockets junit2html
