FROM zjzdy/ubuntu-1604-vslam-base:latest
LABEL maintainer "zjzengdongyang@163.com"

RUN git clone https://github.com/famoreno/stereo-vo.git && cd stereo-vo && \
sed -i "s/FIND_PACKAGE(OpenCV 2/#FIND_PACKAGE(OpenCV 2/g" CMakeLists.txt && \
sed -i "s/#FIND_PACKAGE(OpenCV 3.1.0/FIND_PACKAGE(OpenCV 3/g" CMakeLists.txt && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && \
make install && cd ..