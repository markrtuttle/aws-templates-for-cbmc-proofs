FROM centos:8

ENV PAT=$PATH:/ninja

RUN yum install \
    bison  \
    cmake \
    flex \
    gcc \
    gcc-c++ \
    git \
    jq \
    make \
    maven \
    openjdk \
    patch \
    python3 \
    which

RUN \
    cd / && \
    git clone https://github.com/ninja-build/ninja.git ninja && \
    cd ninja && \
    python3 ./configure.py --bootstrap && \
    ninja --version

RUN \
    cd / && \
    git clone https://github.com/diffblue/cbmc.git cbmc && \
    cd cbmc && \
    mkdir build && \
    cd build && \
    cmake -GNinja .. && \
    ninja && \
    ninja install && \
    cp -r bin cbmc && \
    tar fcz /tmp/cbmc.tar.gz cbmc && \
    rm -rf *
