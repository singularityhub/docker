FROM docker:18.02

############################################################
# Development Base with docker2singularity
# docker build -f Dockerfile.dev -t docker2singularity:dev .
############################################################

RUN apk add --update automake libtool m4 autoconf alpine-sdk linux-headers openssl-dev
RUN apk add --update libuuid squashfs-tools libarchive-dev git python util-linux-dev rsync

# Install Singularity from Github
WORKDIR /tmp
RUN git clone -b vault/release-2.6 https://github.com/sylabs/singularity.git && \
    cd /tmp/singularity && ./autogen.sh && ./configure --prefix=/usr/local && make && make install

WORKDIR /
ADD docker2singularity.sh /docker2singularity.sh
RUN chmod a+x docker2singularity.sh
RUN mkdir -p /usr/local/var/singularity/mnt

ENTRYPOINT ["docker-entrypoint.sh","/docker2singularity.sh"]
