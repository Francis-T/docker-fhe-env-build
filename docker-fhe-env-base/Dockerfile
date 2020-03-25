FROM debian:sid-slim

# Prepare the ubuntu image
RUN apt-get update && apt-get install -y bzip2 cmake g++ make m4 git wget

# Install the required packages
WORKDIR /libs/
# RUN CMAKE_V=3.15.0-rc2 && \
#     wget -q https://github.com/Kitware/CMake/releases/download/v${CMAKE_V}/cmake-${CMAKE_V}.tar.gz && \
#     tar -zxvf cmake-${CMAKE_V}.tar.gz && \
#     cd cmake-${CMAKE_V} && \
#     ./configure && \
#     make -j4 && \
#     make install && \
#     make clean && \
#     cd /libs && \
RUN GMP_V=6.1.2 && \
    wget -q https://gmplib.org/download/gmp/gmp-$GMP_V.tar.bz2 && \
    tar -xjf gmp-$GMP_V.tar.bz2 && \
    rm gmp-$GMP_V.tar.bz2 && \
    cd gmp-$GMP_V && \
    ./configure && \
    make -j4 && \
    make check && \
    make install && \
    make clean && \
    cd /libs && \ 
    NTL_V=10.5.0 && \
    wget -q http://www.shoup.net/ntl/ntl-$NTL_V.tar.gz && \
    tar -xzf ntl-$NTL_V.tar.gz && \
    rm ntl-$NTL_V.tar.gz && \
    cd ntl-$NTL_V/src && \
    ./configure NTL_GMP_LIP=on && \
    make -j4 && \
    make install && \
    make clean && \
    cd /libs && \
    rm -rf ntl-$NTL_V gmp-$GMP_V

WORKDIR /

