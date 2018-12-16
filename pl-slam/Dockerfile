FROM zjzdy/ubuntu-1604-vslam-base:latest
LABEL maintainer "zjzengdongyang@163.com"

RUN apt-get -y update && \
apt-get -y install libboost-all-dev && \
apt-get clean && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN git clone https://github.com/rubengooj/stvo-pl.git && cd stvo-pl && \
cd 3rdparty/line_descriptor && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && \
make install && cd ../../.. && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && \
make install

RUN git clone https://github.com/rubengooj/pl-slam.git && cd pl-slam && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && \
make install