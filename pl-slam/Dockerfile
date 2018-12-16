FROM zjzdy/ubuntu-1604-vslam-base:latest
LABEL maintainer "zjzengdongyang@163.com"

RUN apt-get -y update && \
apt-get -y install libboost-all-dev && \
apt-get clean && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN git clone https://github.com/rubengooj/stvo-pl.git && cd stvo-pl && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && \
make install && cd ..

RUN git clone https://github.com/rubengooj/pl-slam.git && cd pl-slam && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && \
make install && cd ..