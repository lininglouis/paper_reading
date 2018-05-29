###两种detection方法
1 detection by classification 穷举各个位置
优点只要分类器足够优秀，经过穷举后一定可以得到比较好的结果
缺点：计算量比较大

2 regression refinement
给定初始化的图像位置，不断去refine这个位置。
现在的detecton 是在两端做一个tradeoff




###关键点回归和mask回归一个方案
和mask分割一样，比如有17个关键点，那么就输出17个二值mask，每个mask图只标记关键点所在位置。



###多尺度
image pyramid
filter pyramid
anchor pyramid:好处是多尺度可以在同一个featuremap上做操作。 而不需要filterpyramid需要在不同巻积层提取特征。



### ROI align
原图bbox-->feature map bbox-->映射回原图




### 对于小目标的misalignment
我在实验时发现，ROI Align在VOC2007数据集上的提升效果并不如在COCO上明显。经过分析，造成这种区别的原因是COCO上小目标的数量更多，而小目标受misalignment问题的影响更大（比如，同样是0.5个像素点的偏差，对于较大的目标而言显得微不足道，但是对于小目标，误差的影响就要高很多
