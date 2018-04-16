faster rcnn
http://www.360doc.com/content/17/0303/14/10408243_633634497.shtml


1）faster使用conv卷积提取feature map

2）基于feature map将position的位置交给region proposal，使用回归卷积，根据anchorbox 回归出各个anchor box的分类和回归信息。然后提出超边界的foreground anchor， 进行nms，提取符合条件proposal

3）根据feature map和proposal， 提取proposal feature map，对proposal feature map做roi pooling，
进行分类，和bbox 回归获得最终测试框精确位置



1和2可以连续

然后每个region proposal做ROI pooling

3对proposal region做分类和回归
https://arxiv.org/pdf/1603.07285.pdf



