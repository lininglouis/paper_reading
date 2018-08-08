
### 大batch
好处是处理数据速度快，梯度方向能够更明确directly指向极值方向。  
 
坏处是
1. 容易收敛到陡峭极值点sharp minimizer（这样模型的generalization能力就相对比较差 The lack of **generalization ability is due to the fact that large-batch methods tend to converge to sharp minimizers of the training function**   https://arxiv.org/abs/1609.04836 ）。 而小batch则更容易收敛到平滑的极值点。 
2. 达到相同精度，大batch情况需要更多的epoch。 
3. 当batchsize太大的时候，大batch最终收敛的精度可能会比小batch训练达到的精度差(https://arxiv.org/abs/1606.02228)。 


### 小batch
1. 收敛速度慢，有更多的抖动噪声，但是随机探索的范围更广，尝试的空间更多，有更多的机会发现更好的极值点，小batch训练的模型泛化能力更强。
2. 更多的抖动也有助于帮助optimizer远离bad local minima，而不是陷入局部最优. 这种噪声也有些regularization的正则化效果。These results indicate that gradient noise can be beneficial, especially in non-convex optimization. It has been proposed that noise helps SGD escape “sharp minima” which generalize poorly （谷歌论文 https://arxiv.org/pdf/1711.00489.pdf提到）



### Quora
大的网络用大的batch size

### 参考资源
知乎讨论
* https://www.zhihu.com/question/32673260/answer/71137399
* https://zhuanlan.zhihu.com/p/23021473
其他文献
* https://stats.stackexchange.com/questions/164876/tradeoff-batch-size-vs-number-of-iterations-to-train-a-neural-network
* https://arxiv.org/abs/1606.02228  Systematic evaluation of CNN advances on the ImageNet  大模型的泛化generalization能力差
* https://arxiv.org/pdf/1609.04836.pdf  大batch模型会有sharp minima
* https://arxiv.org/pdf/1711.00489.pdf   DON’T DECAY THE LEARNING RATE,  INCREASE THE BATCH SIZE 谷歌大佬论文
* https://www.quora.com/How-do-I-choose-the-appropriate-batch-size-while-training-a-CNN



