FROM hxsoong/kylin:v10-sp3

COPY ./CentOS-SCLo-scl-rh.repo /etc/yum.repos.d/

RUN yum -y install \
    flex \
    bison \
    cmake3 \
    curl \
    findutils \
    libpcap-devel \
    libmaxminddb-devel \
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
    tar \
    xz \
  && yum clean all && rm -rf /var/cache/yum

RUN pip3 install websockets junit2html

ENV CCACHE_VERSION=4.10.2
ENV CCACHE_PLATFORM=linux-x86_64
ENV CCACHE_URL=https://github.com/ccache/ccache/releases/download/v${CCACHE_VERSION}/ccache-${CCACHE_VERSION}-${CCACHE_PLATFORM}.tar.xz
ENV CCACHE_SHA256=80cab87bd510eca796467aee8e663c398239e0df1c4800a0b5dff11dca0b4f18
RUN cd /opt \
    && if [ "$(uname -p)" != "x86_64" ]; then echo "cannot use ccache pre-built for x86_64!" >&2; exit 1 ; fi \
    && curl -L --fail --max-time 30 $CCACHE_URL -o ccache.tar.xz \
    && sha256sum ./ccache.tar.xz >&2 \
    && echo "${CCACHE_SHA256} ccache.tar.xz" | sha256sum -c - \
    && tar xvf ./ccache.tar.xz \
    && ln -s $(pwd)/ccache-${CCACHE_VERSION}-${CCACHE_PLATFORM}/ccache /usr/local/bin/ccache \
    && test "$(command -v ccache)" = "/usr/local/bin/ccache" \
    && test "$(ccache --print-version)" = "${CCACHE_VERSION}" \
    && rm ./ccache.tar.xz

RUN echo 'unset BASH_ENV PROMPT_COMMAND ENV' > /usr/bin/zeek-ci-env && \
    echo 'source /opt/rh/devtoolset-11/enable' >> /usr/bin/zeek-ci-env

ENV BASH_ENV="/usr/bin/zeek-ci-env" \
    ENV="/usr/bin/zeek-ci-env" \
    PROMPT_COMMAND=". /usr/bin/zeek-ci-env"
