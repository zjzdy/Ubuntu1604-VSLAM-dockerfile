FROM zjzdy/ubuntu-1604-vslam-base:latest
LABEL maintainer "zjzengdongyang@163.com"

RUN apt-get -y update && \
apt-get -y install libpcl-dev libproj-dev && \
apt-get clean && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN git clone https://github.com/gaoxiang12/ORBSLAM2_with_pointcloud_map.git && \
cd ORBSLAM2_with_pointcloud_map/ORB_SLAM2_modified && \
rm -rf cmake-build-debug Thirdparty/DBoW2/build Thirdparty/g2o/build && \
mkdir Vocabulary && \
wget https://github.com/raulmur/ORB_SLAM2/raw/master/Vocabulary/ORBvoc.txt.tar.gz -O Vocabulary/ORBvoc.txt.tar.gz && \
sed -i '58a list(REMOVE_ITEM PCL_LIBRARIES "vtkproj4")' CMakeLists.txt && \
sed -i "s/-j/-j2/g" build.sh && \
chmod +x build.sh && \
./build.sh 
