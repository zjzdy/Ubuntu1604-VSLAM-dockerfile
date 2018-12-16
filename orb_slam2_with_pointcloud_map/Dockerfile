FROM zjzdy/ubuntu-1604-vslam-base:latest
LABEL maintainer "zjzengdongyang@163.com"

RUN wget https://github.com/gaoxiang12/ORBSLAM2_with_pointcloud_map/raw/master/orbslam2_modified.zip -O orbslam2_modified.zip && \
unzip -q orbslam2_modified.zip && \
rm orbslam2_modified.zip

RUN cd g2o_with_orbslam2 && \
sed -i "s/setRotation(t.rotation().angle()+_measurement)/setRotation((Eigen::Rotation2Dd)(t.rotation().angle()+_measurement))/g" g2o/types/slam2d/edge_se2_pointxy_bearing.cpp && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && \
cd ..

RUN cd ORB_SLAM2_modified && \
mkdir Vocabulary && \
wget https://github.com/raulmur/ORB_SLAM2/raw/master/Vocabulary/ORBvoc.txt.tar.gz -O Vocabulary/ORBvoc.txt.tar.gz && \
sed -i "s/-j/-j2/g" build.sh && \
chmod +x build.sh && \
./build.sh