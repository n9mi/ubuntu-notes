1. Install prerequities
```
sudo apt install build-essential cmake git pkg-config libgtk-3-dev \
    libavcodec-dev libavformat-dev libswscale-dev libv4l-dev \
    libxvidcore-dev libx264-dev libjpeg-dev libpng-dev libtiff-dev \
    gfortran openexr libatlas-base-dev python3-dev python3-numpy \
    libtbb2 libtbb-dev libdc1394-22-dev libopenexr-dev \
    libgstreamer-plugins-base1.0-dev libgstreamer1.0-dev
```

2. Download from source and place to ~/opencv_build
```
cd ~
mkdir ~/opencv_build
cd ~/opencv_build

wget -O opencv.zip https://github.com/opencv/opencv/archive/4.8.1.zip
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.8.1.zip

unzip opencv.zip
mv opencv-4.8.1 opencv

unzip opencv_contrib.zip
mv opencv-4.8.1_contrib opencv_contrib
```

3. Setup OpenCV build with cmake
```
cd ~/opencv_build/opencv
mkdir -p build && cd build

cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_C_EXAMPLES=ON \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_GENERATE_PKGCONFIG=ON \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_build/opencv_contrib/modules \
    -D BUILD_EXAMPLES=ON ..
```

Output will be:
```
-- Configuring done
-- Generating done
-- Build files have been written to: ${HOME}/opencv_build/opencv/build
```

4. Start compilation process
```
make 
```
Notes: be careful with -j parameter, if you set the -j parameter wrong, example: equal or more than 'nproc', it'll cause your computer to force shutdown. 

5. Finnally, install the opencv
```
sudo make install
```

6. Check opencv installation
```
pkg-config --modversion opencv4
```

7. Installing gocv
```
GO111MODULE=off go get -u -d gocv.io/x/gocv
```

8. Verifying the gocv installation
```
cd ~/go/src/gocv.io/x/gocv
go run ./cmd/version/main.go
```

Output will be:
```
gocv version: 0.35.0
opencv lib version: 4.8.1
```

# Misscelaneous 
## A. Error while loading shared libraries: libopencv_highgui.so.4.4: cannot open shared object file: No such file or directory when running
```
go run ./cmd/version/main.go
```
Solution
1. Ensure that libopencv_mcc.so.408 in present in /usr/local/lib
2. Create configuration in /etc/ld.so.conf.d by
```
sudo nano /etc/ld.so.conf.d/opencv.conf

/usr/local/lib/
```
3. Then run
```
sudo ldconfig -v
```
4. Try run previous command
```
go run ./cmd/version/main.go
```

   
Credit:
- https://linuxize.com/post/how-to-install-opencv-on-ubuntu-20-04/
- https://gocv.io/getting-started/linux/
- https://stackoverflow.com/questions/62621706/libopencv-highgui-so-4-4-cannot-open-shared-object-file-no-such-file-or-direct
