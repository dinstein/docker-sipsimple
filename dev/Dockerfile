FROM ubuntu:xenial

WORKDIR /workdir

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    build-essential autoconf libtool pkg-config \
    git python python-dev python-pip python-setuptools \
    libgmp3-dev libmpc-dev libmpfr-dev libavformat-dev libswscale-dev libvpx-dev libssl-dev libsqlite3-dev libv4l-dev libasound2-dev \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN pip install --upgrade pip \
    && pip install -U python-gnutls python-otr dnspython twisted python-application cython python-dateutil greenlet

RUN git clone https://github.com/AGProjects/python-sipsimple.git \
    && cd python-sipsimple \
    && chmod a+x deps/pjsip/configure deps/pjsip/aconfigure \
    && python setup.py build_ext \
    && python setup.py install \
    && cd .. \

RUN git clone https://github.com/AGProjects/sipclients.git \
    && cd sipclients \
    && python setup.py install \
    && cd .. \
