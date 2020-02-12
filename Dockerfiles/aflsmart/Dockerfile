FROM ubuntu:16.04
RUN apt-get update
MAINTAINER Mohamed NJEH <njeh@eurecom.fr>

RUN apt-get update \
    && apt-get install -y \
        afl git  wget libtool libtool-bin bison libglib2.0-dev build-essential automake libtool libc6-dev-i386
RUN wget https://www.cairographics.org/releases/pixman-0.34.0.tar.gz
RUN tar xvfz pixman-0.34.0.tar.gz
RUN cd pixman-0.34.0 && ./configure --prefix=/usr --disable-static && make && make check && make install
RUN apt-get update \
    && apt-get install -y \
        clang gcc gdb git python-setuptools gcc-multilib python-pip g++-multilib 
RUN rm -r pixman-0.34.0.tar.gz pixman-0.34.0
RUN apt-get update
RUN git clone https://github.com/aflsmart/aflsmart
RUN export CC=afl-gcc
RUN export AFLSMART=$(pwd)/aflsmart
RUN export WORKDIR=$(pwd)
RUN cd aflsmart && make && make install && cp afl-* /usr/local/bin/
RUN cd aflsmart && chmod +x setup_env.sh && ./setup_env.sh
RUN git clone https://github.com/SandPhoenixX517/952558172239733620701363/
RUN mv $(pwd)/952558172239733620701363/aflsmartEmbedded aflsmartEmbedded
RUN chmod +x aflsmartEmbedded


