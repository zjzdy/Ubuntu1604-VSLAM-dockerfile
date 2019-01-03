FROM zjzdy/ubuntu-1604-vslam-base:latest
LABEL maintainer "zjzengdongyang@163.com"

RUN apt-get -y update && \
apt-get -y install libboost-all-dev && \
apt-get clean && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN git clone https://github.com/rubengooj/stvo-pl.git && cd stvo-pl && \
cd 3rdparty/line_descriptor && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc) && cd ../../.. && \
mkdir build && \
cd build && \
cmake .. && \
make -j$(nproc)

RUN git clone https://github.com/RainerKuemmerle/g2o.git && cd g2o && \
mkdir build && cd build && cmake .. && make && make install && rm -rf /g2o

RUN git clone https://github.com/rubengooj/pl-slam.git && cd pl-slam && \
sed -i "s/G2O      REQUIRED/g2o      REQUIRED/g" CMakeLists.txt && \
sed -i "s/g2o_ext_csparse //g" CMakeLists.txt && \
sed -i "s/g2o::BlockSolver_6_3::LinearSolverType\* linearSolver;/std::unique_ptr<g2o::BlockSolver_6_3::LinearSolverType> linearSolver(new g2o::LinearSolverCholmod<g2o::BlockSolver_6_3::PoseMatrixType>());/g" src/mapHandler.cpp && \
sed -i "s/linearSolver = new g2o::LinearSolverCholmod<g2o::BlockSolver_6_3::PoseMatrixType>();//g" src/mapHandler.cpp && \
sed -i "s/g2o::BlockSolver_6_3\* solver_ptr = new g2o::BlockSolver_6_3(linearSolver);/std::unique_ptr<g2o::BlockSolver_6_3> solver_ptr(new g2o::BlockSolver_6_3(std::move(linearSolver)));/g" src/mapHandler.cpp && \
sed -i "s/g2o::OptimizationAlgorithmLevenberg\* solver = new g2o::OptimizationAlgorithmLevenberg(solver_ptr);/g2o::OptimizationAlgorithmLevenberg\* solver = new g2o::OptimizationAlgorithmLevenberg(std::move(solver_ptr));/g" src/mapHandler.cpp && \
chmod +x build.sh && \
./build.sh
