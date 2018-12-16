FROM zjzdy/ubuntu-1604-vslam-base:latest
LABEL maintainer "zjzengdongyang@163.com"

RUN git clone https://github.com/raulmur/ORB_SLAM2.git && cd ORB_SLAM2 && sed -i "s/-j/-j2/g" build.sh && chmod +x build.sh && ./build.sh 