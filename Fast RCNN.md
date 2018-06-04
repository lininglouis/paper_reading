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




对于RCNN
ROI warp 根据Selective Search从原图提取

对于Fast RCNN和Faster RCNN都是从特征图截取的

 
FastRCNN和DeformableConv的ROI pooling都是对featuremap的某个ROI区域进行ROI pooling。
RCNN是针对原图做ROI Warp

FastRCNN的ROIpooling放在ResnetConv4和Conv5之间，
1.对Conv4的特征图进行ROI pooling，
2.针对对每个ROIpooling出的featuremap(HxW),
3.使用Conv5进行进一步特征提取，
4.后输出classification和bbox regression两个Head。

Deformable Conv和FPN里面的从Conv4位置提取ROI，但是ROIPooling之后接的是2个FC，而不是Conv5(你看的Resnet-FPN版本的MaskRcnn里面CropROI那个函数也是用两个FC取代的），
1.将Conv4层进行ROI Pooling，
2.针对对每个ROIpooling出的featuremap(HxW)，
3.然后不接Conv5 层而是直接接两个FC，
4.后输出classification和bbox regression.




原图经过ResnetConv4层得到单尺度的featuremap，针对featuremap某个区域的做ROI pooling，接Resnet的conv5和以后的卷积层，然后输出classification和boxoffset regression这两个。

Deformable Conv采用ROI的思想ROIpooling。我们刚才看的MaskRCNN代码里面的ROIpooling用的其实也是FPN里面的ROI Pooling。


