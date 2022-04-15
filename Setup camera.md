
# Sử dụng camera với ROS
# **Cách 1 (nên dùng)**
### Sử dụng package [ros_astra_camera](https://github.com/orbbec/ros_astra_camera)
### **Bước 1: Cài các chương trình hỗ trợ**
```
sudo apt install ros-$ROS_DISTRO-rgbd-launch ros-$ROS_DISTRO-libuvc ros-$ROS_DISTRO-libuvc-camera ros-$ROS_DISTRO-libuvc-ros
```
### **Bước 2: Clone source code về  Workspace**
```
cd ~/(Tên Workspace)/src
git clone https://github.com/orbbec/ros_astra_camera
cd ..
catkin_make
source devel/setup.bash
```
### **Bước 3: tạo udev rules**
```
roscd astra_camera
chmod 777 /scripts/create_udev_rules
./scripts/create_udev_rules
```

### **Bước 4: Rút camera ra cắm lại và chạy launch file**
```
roslaunch astra_camera astra.launch
```
# **Cách 2**
### **Bước 1: Cài SDK của OPENNI2**
* [Link tải](https://structure.io/openni)
* Giải nén 
 
```
unzip ~/Downloads/OpenNI_2.3.0.66.zip
``` 
* Cài đặt
```
cd ~/Downloads/Linux/OpenNI-Linux-x64-2.3.0.66
sudo ./install.sh
```

### **Bước 2: Cài Ros package cho Openni2**
```
sudo apt-get install ros-$ROS_DISTRO-openni2-camera ros-$ROS_DISTRO-openni2-launch
```
Copy các thư viện cần thiết
```
cd ~/Downloads/Linux/OpenNI-Linux-x64-2.3.0.66/Samples/Bin

sudo cp libOpenNI2.so /usr/lib/libOpenNI2.so
sudo cp OpenNI2/Drivers/* /usr/lib/OpenNI2/Drivers/
```

### **Bước 3: Tải launch file**

```
cd ~/(Tên Workspace)/src
git clone https://github.com/ros-drivers/openni2_camera.git
cd ..
catkin_make
source devel/setup.bash
```

* Chạy launch file để khởi động camera
```
roslaunch openni2_launch openni2.launch
```

# Kiểm tra camera bằng Rviz hoặc rqt_image_view

### **Các topic quan trọng**

* /camera/rgb/image_raw
* /camera/depth/points




