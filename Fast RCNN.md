######



R-CNN
image - proposals - cnn - svm - bb regression

fast rcnn
image - proposals - cnn - roi - classification
                              - bb regression
                         
                         

SPP-net and ROI pooling
can map region of different size to a fixed output feature vector


小目标检测方法
1） 多层尺度回归
2） 小stride 卷积. 常用的网络结构对应的 stride 一般会比较大（如 32），而图像中的小物体甚至会小于 stride 的大小，造成的结果就是小物体的检测性能急剧下降

