FROM python:3.8.1

RUN apt-get update \
    && apt-get install -y \
    autoconf \
    automake \
    cmake \
    curl \
    g++ \
    git \
    graphviz \
    libatlas3-base \
    libtool \
    make \
    pkg-config \
    subversion \
    unzip \
    wget \
    zlib1g-dev \
    && pip install --upgrade pip numpy setuptools pyparsing ninja \
    && git clone https://github.com/pykaldi/pykaldi.git \
    && cd pykaldi/tools \
    && ./check_dependencies.sh \
    && ./install_protobuf.sh \
    && ./install_clif.sh \
    && ./install_kaldi.sh \
    && cd .. \
    && python setup.py install \
    && cd / \
    && rm -rf /pykaldi
