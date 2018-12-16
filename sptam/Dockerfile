FROM zjzdy/ubuntu-1604-vslam-base:ros
LABEL maintainer "zjzengdongyang@163.com"

RUN apt-get -y update && \
apt-get -y install 	ros-kinetic-tf2-geometry-msgs libgtest-dev && \
apt-get clean && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN bash -c "mkdir /sptam && cd /sptam && source /opt/ros/kinetic/setup.bash && \
mkdir src && cd src && \
git clone https://github.com/lrse/ros-utils.git && cd ros-utils && \
mkdir build && cd build && cmake .. && make && make install && cd ../.. && \
git clone https://github.com/RainerKuemmerle/g2o.git && cd g2o && \
git checkout 4b9c2f5b68d14ad479457b18c5a2a0bce1541a90 && \
mkdir build && cd build && cmake .. && make && make install && cd ../.. && \
git clone https://github.com/dorian3d/DLib.git && cd DLib && \
git checkout 70089a38056e8aebd5a2ebacbcb67d3751433f32 && \
mkdir build && cd build && cmake .. && make && make install && cd ../.. && \
git clone https://github.com/dorian3d/DBoW2.git && cd DBoW2 && \
git checkout 82401cad2cfe7aa28ee6f6afb01ce3ffa0f59b44 && \
mkdir build && cd build && cmake .. && make && make install && cd ../.. && \
git clone https://github.com/dorian3d/DLoopDetector.git && cd DLoopDetector && \
git checkout 8e62f8ae84d583d9ab67796f779272b0850571ce && \
mkdir build && cd build && cmake .. && make && make install && cd ../.. && \
git clone https://github.com/laurentkneip/opengv.git && cd opengv && \
git checkout 2e2d21917fd2fb75f2134e6d5be7a2536cbc7eb1 && \
mkdir build && cd build && cmake .. && make && make install && cd ../.. && \
rm -rf ros-utils g2o DLib DBoW2 DLoopDetector opengv && \
git clone https://github.com/lrse/sptam.git && cd sptam && git submodule update --init --recursive
RUN cd /sptam && catkin_make --pkg sptam -DCMAKE_BUILD_TYPE=RelWithDebInfo -DUSE_LOOPCLOSURE=ON -DSINGLE_THREAD=OFF -DSHOW_TRACKED_FRAMES=ON -DSHOW_PROFILING=ON -DPARALLELIZE=ON"
