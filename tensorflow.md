tensorflow


unnormalized logtis probabilitys  means logits
normalized logis means softmaxed logits
do calculation of predicted logits and ground truth label logits.  use  tf.softmax_cross_entropy_with_logits(logits, labels)


Variable是可更改的（mutable），而Tensor是不可更改的。一个直接的例子就是Tensor不具有assign函数，而Variable含有。
python和其他语言的API以及实现方式存在差异，本文只探讨general以及python方面的内容。
Variable用于存储网络中的权重矩阵等变量，而Tensor更多的是中间结果等。
Variable是会显示分配内存空间的（既可以是内存，也可以是显存），需要初始化操作（assign一个tensor），由Session管理，可以进行存储、读取、更改等操作。相反地，诸如Const, Zeros等操作创造的Tensor，是记录在Graph中，所以没有单独的内存空间；而其他未知的由其他Tensor操作得来的Tensor则是只会在程序运行中间出现。
Tensor可以使用的地方，几乎都可以使用Variable。
