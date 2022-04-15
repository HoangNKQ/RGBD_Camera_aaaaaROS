# **A. CV_bridge**
ROS trao đổi dữ liệu hình ảnh giữa các node bằng cách sử dụng message dạng [sensor_msgs/Image](http://docs.ros.org/en/api/sensor_msgs/html/msg/Image.html). Tuy nhiên, để có thể sử dụng OpenCV xử lý hình ảnh, Image message phải được chuyển đổi về dạng Mat của OpenCV

![alt text](cv_bridge.png) 
### **1. Cài đặt CV_bridge**
Package [vision_opencv](https://github.com/ros-perception/vision_opencv)

```
cd ~/(Tên Workspace)/src
git clone https://github.com/ros-perception/vision_opencv
cd ..
catkin_make
source devel/setup.bash
```
### **2. Chuyển đổi giữa ROS Image message và OpenCV Mat**
* Chuyển từ ROS Image message sang OpenCV Mat
``` Python
from cv_bridge import CvBridge
bridge = CvBridge()
cv_image = bridge.imgmsg_to_cv2(image_message, desired_encoding='passthrough')
```
* Chuyển từ OpenCV Mat sang ROS Image message
```Python
from cv_bridge import CvBridge
bridge = CvBridge()
image_message = bridge.cv2_to_imgmsg(cv_image, encoding="passthrough")
```

* Đọc thêm: [ROS CV_Bridge](http://wiki.ros.org/cv_bridge/Tutorials/ConvertingBetweenROSImagesAndOpenCVImagesPython)
# **A. Astra Camera và OpenCV**
Ví dụ trích xuất ảnh màu từ Astra Camera (Topic /camera/rgb/image_raw)

* Tạo một package mới trong Workspace có tên là test_astra

```
cd ~/(Tên Workspace)/src
catkin_create_pkg test_astra rospy std_msgs sensor_msgs cv_bridge
```
* Tạo thư mục scripts để chứa script python có tên image_pub_sub.py
```
cd test_astra
mkdir scripts
cd scripts
touch image_pub_sub.py

```