######



R-CNN
image - proposals - cnn - svm - bb regression

fast rcnn
image - proposals - cnn - roi - classification
                              - bb regression
                         

get ROI from feature map of any input image size.  对于任意大小的图片，生成的region proposal，都能够通过ROI pooling提取固定维度的信息
ROI pooling 是针对于feature map中的ROI区域做pooling操作



SPP-net and ROI pooling
can map region of different size to a fixed output feature vector


小目标检测方法
1） 多层尺度回归
2） 小stride 卷积. 常用的网络结构对应的 stride 一般会比较大（如 32），而图像中的小物体甚至会小于 stride 的大小，造成的结果就是小物体的检测性能急剧下降



fastrcnn相对rcnn改进： 一个是roi pooling 一个是图像和特征处理顺序
1）采纳sppnet，能够通过roi pooling 对不同尺寸图片提取固定维度的特征，而不是将图像warp成固定大小。
2）fastrcnn先进行卷积计算feature map特征图，然后再对ss生成的proposal提取固定长度的特征。。 而rcnn是先生成ss，然后针对roi的影像进行warp，feature extraction和特征提取。 
