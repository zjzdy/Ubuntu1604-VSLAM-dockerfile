FROM zjzdy/ubuntu-1604-vslam-base:ros
LABEL maintainer "zjzengdongyang@163.com"

RUN bash source "/opt/ros/kinetic/setup.bash" && git clone https://github.com/ANYbotics/kindr.git && \
cd kindr && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && \
cd ..

RUN bash source "/opt/ros/kinetic/setup.bash" && git clone https://github.com/ethz-asl/rovio.git && \
git submodule update --init --recursive && \
catkin build rovio --cmake-args -DCMAKE_BUILD_TYPE=Release