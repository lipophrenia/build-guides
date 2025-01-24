# OpenCV build from sources

Install minimal prerequisites.
```bash
sudo apt update && sudo apt install -y cmake g++ wget unzip
```
Download and unpack sources.
```bash
wget -O opencv.zip https://github.com/opencv/opencv/archive/4.x.zip
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.x.zip
unzip opencv.zip
unzip opencv_contrib.zip
```
Create build directory.
```bash
mkdir build && cd build
```
Configure. [Config reference](https://docs.opencv.org/4.9.0/db/d05/tutorial_config_reference.html).
```bash
# BASE CONFIG
cmake -DOPENCV_EXTRA_MODULES_PATH=../opencv_contrib-4.x/modules  \
-DCMAKE_INSTALL_PREFIX=/usr/local \
-DCMAKE_BUILD_TYPE=RELEASE \
-DBUILD_EXAMPLES=OFF \
-DBUILD_PERF_TESTS=OFF \
-DBUILD_TESTS=OFF \
-DBUILD_opencv_apps=OFF \
-DBUILD_SHARED_LIBS=ON \
-DOPENCV_GENERATE_PKGCONFIG=ON \
-DBUILD_JAVA=OFF \
-DENABLE_FAST_MATH=ON \
-DOPENCV_ENABLE_NONFREE=ON \
-DWITH_GSTREAMER=ON \
../opencv-4.x
```
```bash
# MY CONFIG
cmake -DOPENCV_EXTRA_MODULES_PATH=../opencv_contrib-4.x/modules  \
-DCMAKE_INSTALL_PREFIX=/usr/local \
-DCMAKE_BUILD_TYPE=RELEASE \
-DBUILD_EXAMPLES=OFF \
-DBUILD_PERF_TESTS=OFF \
-DBUILD_TESTS=OFF \
-DBUILD_opencv_apps=OFF \
-DBUILD_SHARED_LIBS=ON \
-DOPENCV_GENERATE_PKGCONFIG=ON \
-DBUILD_JAVA=OFF \
-DENABLE_FAST_MATH=ON \
-DOPENCV_ENABLE_NONFREE=ON \
# requires libeigen3-dev from apt
-DWITH_EIGEN=ON \
-DWITH_GSTREAMER=ON \
# requires qt packages from apt
-DWITH_QT=ON \
-DWITH_OPENGL=ON \
# requires ccache from apt
-DENABLE_CCACHE=ON \
# requires Nvidia CUDA Toolkit and CUDNN
#-DOPENCV_DNN_CUDA=ON \
-DWITH_CUDA=ON \
# Search for your GPU
-DCUDA_ARCH_BIN=8.6 \
-DCUDA_ARCH_PTX=8.6 \
# requires Nvidia Video Codec SDK
-DWITH_NVCUVENC=ON \
-DWITH_NVCUVID=ON \
../opencv-4.x
```
Build and install.
```bash
make -j$(nproc)
sudo make install
```
