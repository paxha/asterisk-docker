FROM ubuntu:21.10

LABEL maintainer="Hassan Raza Pasha"

ENV ASTERISK_VERSION 19

WORKDIR /etc/asterisk

RUN apt update  \
    && apt upgrade -y \
    && apt install -y --no-install-recommends --no-install-suggests \
      autoconf \
      binutils-dev \
      build-essential \
      ca-certificates \
      wget \
      curl \
      file \
      libcurl4-openssl-dev \
      libedit-dev \
      libgsm1-dev \
      libogg-dev \
      libpopt-dev \
      libresample1-dev \
      libspandsp-dev \
      libspeex-dev \
      libspeexdsp-dev \
      libsqlite3-dev \
      libsrtp2-dev \
      libssl-dev \
      libvorbis-dev \
      libxml2-dev \
      libxslt1-dev \
      odbcinst \
      portaudio19-dev \
      procps \
      unixodbc \
      unixodbc-dev \
      uuid \
      uuid-dev \
      xmlstarlet \
    && cd /usr/src/ \
    && wget http://downloads.asterisk.org/pub/telephony/asterisk/asterisk-${ASTERISK_VERSION}-current.tar.gz \
    && tar zxf asterisk-${ASTERISK_VERSION}-current.tar.gz \
    && cd asterisk-${ASTERISK_VERSION}.*/ \
    && ./configure --with-pjproject-bundled --with-jansson-bundled \
    && make menuselect/menuselect menuselect-tree menuselect.makeopts \
    && make -j $(nproc) \
    && make install \
    && make samples \
    && sed -i -E 's/^;(run)(user|group)/\1\2/' /etc/asterisk/asterisk.conf \
    && useradd --system asterisk \
    && chown -R asterisk:asterisk /etc/asterisk \
                                  /var/*/asterisk \
                                  /usr/*/asterisk \
    && chmod -R 750 /var/spool/asterisk

EXPOSE 5060/udp

CMD ["asterisk", "-vvvdddf"]
