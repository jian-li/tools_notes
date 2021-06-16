# `opencv`编译遇到的那些坑
## `opencv_contrib`编译失败
在编译`opencv_contrib`模块的时候，需要打开`ccmake`下面的`opencv_enable_nonfree`选项。
在`opencv_contrib/modules/xfeatures2d/src`目录下：
```

curl https://raw.githubusercontent.com/cbalint13/opencv-dlco/master/workspace/opencv/vgg_generated_120.i > vgg_generated_120.i -x http://127.0.0.1:1088
curl https://raw.githubusercontent.com/cbalint13/opencv-dlco/master/workspace/opencv/vgg_generated_48.i > vgg_generated_48.i -x http://127.0.0.1:1088
curl https://raw.githubusercontent.com/cbalint13/opencv-dlco/master/workspace/opencv/vgg_generated_64.i > vgg_generated_64.i -x http://127.0.0.1:1088
curl https://raw.githubusercontent.com/cbalint13/opencv-dlco/master/workspace/opencv/vgg_generated_80.i > vgg_generated_80.i -x http://127.0.0.1:1088
curl https://raw.githubusercontent.com/opencv/opencv_3rdparty/34e4206aef44d50e6bbcd0ab06354b52e7466d26/boostdesc_bgm.i > boostdesc_bgm.i
curl https://raw.githubusercontent.com/opencv/opencv_3rdparty/34e4206aef44d50e6bbcd0ab06354b52e7466d26/boostdesc_bgm.i > boostdesc_bgm.i -x http://127.0.0.1:1088
curl https://raw.githubusercontent.com/opencv/opencv_3rdparty/34e4206aef44d50e6bbcd0ab06354b52e7466d26/boostdesc_binboost_064.i > boostdesc_binboost_064.i -x http://127.0.0.1:1088
curl https://raw.githubusercontent.com/opencv/opencv_3rdparty/34e4206aef44d50e6bbcd0ab06354b52e7466d26/boostdesc_bgm_bi.i > boostdesc_bgm_bi.i -x http://127.0.0.1:1088
curl https://raw.githubusercontent.com/opencv/opencv_3rdparty/34e4206aef44d50e6bbcd0ab06354b52e7466d26/boostdesc_bgm_hd.i > boostdesc_bgm_hd.i -x http://127.0.0.1:1088
curl https://raw.githubusercontent.com/opencv/opencv_3rdparty/34e4206aef44d50e6bbcd0ab06354b52e7466d26/boostdesc_binboost_128.i > boostdesc_binboost_128.i -x http://127.0.0.1:1088
curl https://raw.githubusercontent.com/opencv/opencv_3rdparty/34e4206aef44d50e6bbcd0ab06354b52e7466d26/boostdesc_binboost_256.i > boostdesc_binboost_256.i -x http://127.0.0.1:1088
```
关闭测试项：
```
cmake -DBUILD_TESTS=OFF ...
```