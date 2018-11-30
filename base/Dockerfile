FROM docker:18.02

##########################################
# Singularity Base
# docker build -t vanessa/singularity
##########################################

RUN apk add --update automake libtool m4 autoconf alpine-sdk linux-headers openssl-dev
RUN apk add --update libuuid squashfs-tools libarchive-dev git python util-linux-dev rsync

# Install Singularity from Github
WORKDIR /tmp
RUN git clone -b vault/release-2.6 https://github.com/sylabs/singularity.git && \
    cd /tmp/singularity && ./autogen.sh && ./configure --prefix=/usr/local && make && make install

WORKDIR /
RUN mkdir -p /usr/local/var/singularity/mnt

ENTRYPOINT ["docker-entrypoint.sh","singularity"]

ENTRYPOINT ["singularity"]
