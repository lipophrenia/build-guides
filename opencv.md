# OpenCV build from sources

Install minimal prerequisites.
```bash
sudo apt update && sudo apt install -y cmake g++ wget unzip

# If you want to build OpenCV with EIGEN and CCACHE
sudo apt install libeigen3-dev ccache
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
cmake -DOPENCV_EXTRA_MODULES_PATH=../opencv_contrib-4.x/modules \
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
../opencv-4.x

# For EIGEN and CCACHE add these flags before ../opencv-4.x.
-DWITH_EIGEN=ON \
-DENABLE_CCACHE=ON \

# For CUDA add these flags before ../opencv-4.x. Cuda-toolkit and libcudnn-dev required.
# Also you should download NVIDIA Video Codec SDK.
-DOPENCV_DNN_CUDA=ON \
-DWITH_CUDA=ON \
```
Build and install.
```bash
make -j8
sudo make install
```
