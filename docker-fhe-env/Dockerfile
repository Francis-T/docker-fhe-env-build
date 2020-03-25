FROM francisjt/docker-fhe-env-base:latest

# Install the SEAL library
#   *NOTE: v3.2.0 is used because the current version of g++ in 
#          Debian (Stretch-Slim) is only up to v6.0
#
RUN SEAL_V=3.3.0 && cd /libs && \
    git clone https://github.com/microsoft/SEAL.git && \
    cd SEAL && \
    git checkout ${SEAL_V} && \ 
    cd native/src && \
    cmake -DSEAL_USE_CXX17=1 . && \
    make -j4 && \
    make install && \
    make clean

# Install the HEAAN library
#   * NOTE: This installs the original version of the HEAAN lib
#
RUN cd /libs && \
    git clone https://github.com/kimandrik/HEAAN.git && \
    cd HEAAN/HEAAN/lib/ && \
    make -j4 && \
    cp libHEAAN.a /usr/local/lib && \
    mkdir /usr/local/include/HEAAN && \
    cp ../src/*.h /usr/local/include/HEAAN/ 

WORKDIR /

