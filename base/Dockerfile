FROM ubuntu:16.04

##########################################
# Singularity Base
##########################################

RUN apt-get update && \
    apt-get -y install git \
                   build-essential \
                   libtool \
                   squashfs-tools \
                   autotools-dev \
                   automake \
                   libarchive-dev \
                   autoconf \
                   debootstrap \
                   yum \
                   uuid-dev \
                   libssl-dev \
                   python3-pip


# Install Singularity from Github
WORKDIR /tmp
RUN git clone https://github.com/singularityware/singularity.git && \
    cd /tmp/singularity && ./autogen.sh && ./configure --prefix=/usr/local && make && make install

WORKDIR /
RUN mkdir -p /usr/local/var/singularity/mnt

ENTRYPOINT ["singularity"]
