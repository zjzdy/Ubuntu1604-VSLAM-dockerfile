FROM zjzdy/ubuntu-1604-vslam-base:latest
LABEL maintainer "zjzengdongyang@163.com"

RUN apt-get -y update && \
apt-get -y install libopencv-core-dev libopencv-highgui-dev libopencv-video-dev libopencv-features2d-dev && \
apt-get clean && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN git clone https://github.com/famoreno/stereo-vo.git && cd stereo-vo && \
sed -i "s/OpenCV 2.4.5/OpenCV 2.4/g" CMakeLists.txt && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && \
make install