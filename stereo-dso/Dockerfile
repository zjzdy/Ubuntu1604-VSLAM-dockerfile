FROM zjzdy/ubuntu-1604-vslam-base:latest
LABEL maintainer "zjzengdongyang@163.com"

RUN git clone https://github.com/JiatianWu/stereo-dso.git && cd stereo-dso && git submodule update --init

RUN apt-get -y update && \
apt-get -y install zlib1g-dev libboost-system-dev libboost-thread-dev && \
apt-get clean && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN cd stereo-dso/thirdparty && \
tar -zxvf libzip-1.1.1.tar.gz && \
cd libzip-1.1.1/ && \
./configure && \
make && \
make install && \
cp lib/zipconf.h /usr/local/include/zipconf.h

RUN mkdir stereo-dso/build && cd stereo-dso/build && \
cmake .. && \
make -j$(nproc) && \
make install