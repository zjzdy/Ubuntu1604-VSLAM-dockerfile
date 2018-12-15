FROM zjzdy/ubuntu-1604-vslam-base:latest
LABEL maintainer "zjzengdongyang@163.com"

RUN git clone https://github.com/JiatianWu/stereo-dso.git && git submodule update --init

RUN apt-get -y update && \
apt-get -y install zlib1g-dev && \
apt-get clean && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN cd dso/thirdparty && \
tar -zxvf libzip-1.1.1.tar.gz && \
cd libzip-1.1.1/ && \
./configure && \
make && \
sudo make install && \
sudo cp lib/zipconf.h /usr/local/include/zipconf.h

RUN cd .. && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && \
make install