# LeNet

- 获取图像中的结构信息
  
  > 利用图像物体的平移不变性 + 局部性
  > 
  > 使用卷积层，代替全连接层，可获取图像中的 2D 结构信息。
  > 
  > 优势：由于共享参数，所以参数更少。

- LeNet-5 组成
  
  > 2 + 3 结构
  > 
  > 2个卷积层
  > 
  > 3个全连接层
  > 
  > 其中
  > 
  > 1. 卷积层 / 全连接层，都是做线性变换，因此每个层后面都跟一个 sigmod 函数，提供非线性。
  > 
  > 2. 卷积层，在非线性之后，再加一个汇聚层，做数据降维。

- 输入 / 输出
  
  > 输入：手写数字
  > 
  > 输出：0-9 每个可能结果的概率

- 网络结构
  
  > 卷积层：增加通道数。高宽，根据 kernerl_size, padding, stride 调整
  > 
  > 汇聚层：高宽分别减半，每个通道的元素个数为原来的 1/4 ，即25%
  > 
  > 特征形状拉平：将一个样本的所有特征元素，拉平为 1 维度的向量。以便做全连接
  > 
  > 全连接层：减少 1维向量的维度。最终每个样本，降至 10 个值。表示 0-9 这 10个数字的概率分别是多少。

参考：

[LeNet, 动手学深度学习](https://zh.d2l.ai/chapter_convolutional-neural-networks/lenet.html)