FROM zjzdy/ubuntu-1604-vslam-base:ros
LABEL maintainer "zjzengdongyang@163.com"

RUN apt-get -y update && \
apt-get -y install 	python-catkin-tools && \
apt-get clean && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN mkdir rovio_ws && mkdir rovio_ws/src

RUN bash -c "cd rovio_ws/src && source /opt/ros/kinetic/setup.bash && git clone https://github.com/ANYbotics/kindr.git && \
cd kindr && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && \
cd .."

RUN bash -c "cd rovio_ws/src && source /opt/ros/kinetic/setup.bash && \
git clone https://github.com/ethz-asl/rovio.git && cd rovio && \
git submodule update --init --recursive && \
cd ../.. && \
catkin build rovio --cmake-args -DCMAKE_BUILD_TYPE=Release"