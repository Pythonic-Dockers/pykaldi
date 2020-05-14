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
    sox \
    subversion \
    unzip \
    wget \
    zlib1g-dev \
    && pip install --upgrade pip numpy setuptools pyparsing jupyter ninja \
    && cd / \
    && git clone https://github.com/pykaldi/pykaldi.git \
    # && cd /pykaldi/tools \
    && git clone -b pykaldi https://github.com/pykaldi/kaldi.git \
    && cd kaldi/tools \
    && mkdir -p python \
    && touch python/.use_default_python \
    && make -j12 openfst OPENFST_CONFIGURE="--enable-shared --enable-bin --disable-dependency-tracking" \
    && rm -rf openfst/src/script/.libs \
    && cd ../src \
    && ./configure --shared \
    # && make -j12 depend \
    # && make -j12 base matrix util feat tree gmm transform sgmm2 fstext hmm lm decoder lat cudamatrix nnet2 nnet3 rnnlm chain ivector online2 kws \
    && make -j12 \
    && find . -name "*.a" -delete \
    && find . -name "*.o" -delete \
    # && cd /pykaldi/tools \
    && cd / \
    && git clone https://github.com/google/protobuf.git protobuf \
    && cd protobuf \
    && ./autogen.sh \
    && ./configure --prefix /usr --disable-static --disable-dependency-tracking \
    && make -j12 \
    && make install \
    && cd python \
    && python setup.py build \
    && python setup.py install \
    # && cd /pykaldi/tools \
    && cd / \
    && rm -rf protobuf \
    && cd /pykaldi/tools/ \
    && ./install_clif.sh \
    && rm -rf clif_backend \
    && rm -rf clif \
    && rm -rf /pykaldi
    # && cd /pykaldi \
    # && python setup.py develop
