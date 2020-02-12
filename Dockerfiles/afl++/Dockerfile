FROM ubuntu:16.04
RUN apt-get update
MAINTAINER Mohamed Njeh & Ala Tarhouni  <njeh@eurecom.fr> <tarhouni@eurecom.fr>
RUN apt-get update \
    && apt-get install -y \
        afl
RUN apt-get update
RUN apt-get update \
    && apt-get install -y \
        libtool libtool-bin bison libglib2.0-dev wget gcc-multilib
RUN wget https://www.cairographics.org/releases/pixman-0.34.0.tar.gz
RUN tar xvfz pixman-0.34.0.tar.gz
RUN cd pixman-0.34.0 && ./configure --prefix=/usr --disable-static && make && make check && make install
RUN apt-get update \
    && apt-get install -y \
        clang gcc gdb git python-setuptools
RUN rm -r pixman-0.34.0.tar.gz pixman-0.34.0
RUN git clone https://github.com/vanhauser-thc/AFLplusplus.git 
RUN cd AFLplusplus/llvm_mode && install afl-clang-fast.c /usr/bin/afl-clang-fast
RUN cd AFLplusplus && make install && cp afl-* /usr/local/bin/
RUN git clone https://github.com/SandPhoenixX517/952558172239733620701363/
RUN mv $(pwd)/952558172239733620701363/aflppEmbedded aflppEmbedded
RUN chmod +x aflppEmbedded

