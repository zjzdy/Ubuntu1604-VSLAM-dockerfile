FROM ubuntu:16.04
LABEL maintainer "zjzengdongyang@163.com"
ENV OPENCV_VERSION 3.4.4

# Install all dependencies
RUN apt-get -y update && \
apt-get -y install \
libgtk2.0-dev \
libjpeg-dev libjasper-dev libpng-dev libtiff-dev \
libopenexr-dev cmake python-dev \
python-numpy python-tk libtbb-dev \
libeigen2-dev libeigen3-dev yasm libfaac-dev \
libopencore-amrnb-dev libopencore-amrwb-dev \
libtheora-dev libvorbis-dev libxvidcore-dev \
libx264-dev libqt4-dev libqt4-opengl-dev \
sphinx-common libv4l-dev libdc1394-22-dev \
libavcodec-dev libavformat-dev libswscale-dev \
libglew-dev libboost-dev libboost-python-dev libboost-serialization-dev \
htop nano wget git unzip \
python3  python3-dev \
build-essential \
pkg-config \
libatlas-base-dev \
gfortran \
libyaml-cpp-dev \
libsuitesparse-dev \
libmrpt-dev \
&& \
apt-get clean && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
wget https://bootstrap.pypa.io/get-pip.py && \
python3 get-pip.py && \
rm get-pip.py && \
pip3 install numpy

# Install OpenCV
RUN wget https://github.com/opencv/opencv/archive/$OPENCV_VERSION.zip -O opencv3.zip && \
unzip -q opencv3.zip && \
mv /opencv-$OPENCV_VERSION /opencv && \
rm opencv3.zip && \
wget https://github.com/opencv/opencv_contrib/archive/$OPENCV_VERSION.zip -O opencv_contrib3.zip && \
unzip -q opencv_contrib3.zip && \
mv /opencv_contrib-$OPENCV_VERSION /opencv_contrib && \
rm opencv_contrib3.zip \
&& \
mkdir /opencv/build && cd /opencv/build && \
cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D BUILD_PYTHON_SUPPORT=ON \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D OPENCV_EXTRA_MODULES_PATH=/opencv_contrib/modules \
-D BUILD_EXAMPLES=OFF \
-D PYTHON_DEFAULT_EXECUTABLE=/usr/bin/python3 \
-D BUILD_opencv_python3=ON \
-D BUILD_opencv_python2=OFF \
-D WITH_IPP=OFF \
-D WITH_FFMPEG=ON \
-D WITH_V4L=ON .. \
&& \
cd /opencv/build && \
make -j$(nproc) && \
make install && \
ldconfig && \
cd / && \
rm -rf /opencv /opencv_contrib

# Install Pangolin
RUN git clone https://github.com/stevenlovegrove/Pangolin.git && \
cd Pangolin && mkdir build && cd build && cmake .. && \
make -j$(nproc) && \
make install && \
ldconfig && \
cd / && \
rm -rf /Pangolin