优点： 
* 考虑了尺度ratio的问题，而不是在自然数空间内猜。 相比pyramid of images, anchor机制采用的是pyramid of filters，这样共享同一个scale的featuremap，仍然可以使用不同尺度的anchorbox提取不同尺度的信息，(相比pyramid of images方法)，计算量较小，速度快。cost effective （fasterrcnn paper说的）

缺点： 
* 暴力猜，计算量大：还是暴力猜，conv4feature之后加3×3卷积滑动窗口得到的featuremap图,然后每个像素生成固定（3ratio 3 sscale）的anchorbox，加起来有好几千个anchorbox，还要计算和GTbox的overlap， 计算量还是挺大的感觉。
* 合适的anchor的scale和ratio: anchor的大小不一定就是3ratio 3scale。yolov2可以结合ground truth object的大小和ratio信息进行非监督聚类，确定合适的ratio和scale。 而且yolov2只是每个grid cell生成9个anchorbox，默认加起来 7*7(gridcell) * 9 = 441个anchorbox，不是那么多，可能这样才速度快些。
Yolo anchor实现的讨论 https://github.com/pjreddie/darknet/issues/568
