# Install OpenCV on Mac OS

main reference: https://docs.opencv.org/master/d0/db2/tutorial_macos_install.html

## install `Homebrew`

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

## install `cmake`

brew install cmake

## check `cmake` version

cmake --version

## install `python`

brew install python

## check `python` version

python --version

## install `numpy` package of `python`

pip install numpy

## set working directory and clone OpenCV repository from github using `git`

mkdir <my_working_directory>

cd ~/<my_working_directory>

git clone https://github.com/opencv/opencv.git

(optional)git clone https://github.com/opencv/opencv_contrib.git

## make a temporatory directory

mkdir build_opencv

cd build_opencv

## configuring using `cmake`

cmake -DBUILD_TIFF=ON \
  -DBUILD_opencv_java=OFF \
  -DWITH_CUDA=OFF \
  -DWITH_OPENGL=ON \
  -DWITH_OPENCL=ON \
  -DWITH_IPP=ON \
  -DWITH_TBB=ON \
  -DWITH_EIGEN=ON \
  -DWITH_V4L=ON \
  -DBUILD_TESTS=OFF \
  -DBUILD_PERF_TESTS=OFF \
  -DCMAKE_BUILD_TYPE=RELEASE \
  -DCMAKE_INSTALL_PREFIX=$(python -c "import sys; print(sys.prefix)") \
  -DPYTHON_EXECUTABLE=$(which python) \
  -DPYTHON_INCLUDE_DIR=$(python -c "from distutils.sysconfig import get_python_inc; print(get_python_inc())") \
  -DPYTHON_PACKAGES_PATH=$(python -c "from distutils.sysconfig import get_python_lib; print(get_python_lib())") \
  .. 

## Build

make

### optional to check how many cores in Mac

sysctl hw.physicalcpu hw.logicalcpu

make -j7  #runs 7 jobs in parallel
