FROM ubuntu:16.04

WORKDIR /root/

### Install dependencies
RUN sed -i 's/archive.ubuntu.com/ftp.daumkakao.com/g' /etc/apt/sources.list && \
    sed -i 's/# deb-src http:\/\/ftp.daum/deb-src http:\/\/ftp.daum/g' \
      /etc/apt/sources.list && \
    apt-get update && \
    apt-get -yy install \
# Basic utilities
      wget apt-transport-https \
      sudo vim git unzip xz-utils ntp \
      build-essential time libtool libtool-bin gdb \
      automake autoconf bison flex \
# Dependencies for KLEE
      libcap-dev cmake libncurses5-dev python-minimal python-pip \
# Dependencies for LAVA
      libacl1-dev gperf && \
# Dependencies for QEMU used in Eclipser
    apt-get -yy build-dep qemu && \
# Dependencies for Debian packages
    apt-get -yy install lua5.1 autogen && \
    apt-get -yy build-dep ufraw-batch icoutils vorbis-tools gnuplot-nox \
      optipng dcraw wavpack gocr advancecomp x264 jhead sextractor gifsicle && \
# Install .NET Core for Eclipser
    wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb && \
    dpkg -i packages-microsoft-prod.deb && \
    apt-get update && apt-get -yy install dotnet-sdk-2.1 && \
    rm -f packages-microsoft-prod.deb
# pip installation raises an error when combined together
RUN pip install --upgrade pip
RUN pip install --upgrade wllvm

# Create a user and switch.
RUN useradd -ms /bin/bash EUREFUZZ && \
    adduser EUREFUZZ sudo && \
    echo "EUREFUZZ ALL = NOPASSWD : ALL" >> /etc/sudoers
USER EUREFUZZ
WORKDIR /home/EUREFUZZ
# Install Eclipser
RUN git clone https://github.com/SoftSec-KAIST/Eclipser.git && \
    cd Eclipser && \
    git checkout tags/v0.1 && \
    make && \
    rm -rf ./Instrumentor/qemu/qemu-2.3.0*
RUN cd ../
RUN git clone https://github.com/SandPhoenixX517/952558172239733620701363/
RUN mv $(pwd)/952558172239733620701363/eclipserEmbedded eclipserEmbedded
RUN chmod +x eclipserEmbedded

