#可视化相关的工具

## opencv的图像看像素值
`opencv`和`qt`一起编译之后，能够再显示图像的时候放大看到像素值，方法如下：
```
sudo apt install qt5-default
#编译opencv
cmake .. -DWITH_QT=ON && make -j4
```