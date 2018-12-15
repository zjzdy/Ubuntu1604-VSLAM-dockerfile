FROM zjzdy/ubuntu-1604-vslam-base:latest
LABEL maintainer "zjzengdongyang@163.com"

RUN git clone https://github.com/famoreno/stereo-vo.git && cd stereo-vo && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && \
make install && cd ..