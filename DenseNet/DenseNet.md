##### DenseNet

> 密度卷积网络, Dense Convolution Network
> 
> 个人理解：是密度连接，网络结构上，每一层的输出，都会直接连接到之后的每一层，形成紧密的连接。
> 
> 这是特征复用的思想，有压缩模型的效果

- 映射函数
  
  > ResNet 的映射函数
  > 
  > $$
  > X_{l} = H_{l}(X_{l-1}) + X_{l-1}
  > $$
  > 
  > DenseNet 映射函数
  > 
  > $$
  > X_{l} = H_{l}([X_{0}, X_{1}, ... , X_{l-1}])
  > $$

- 稠密块
  
  > 稠密块，包含多个卷积层
  > 
  > 每个卷积层，不改变特征图的高 / 宽，并且输出的通道数相同。
  > 
  > 不同的是，输入通道数。每个卷积层的输出都和输入连接，作为下一层卷积层的输入。
  > 
  > 每个卷积层的通道数的映射
  > 
  > $$
  > C_{in} + C_{out} * i \to C_{out}
  > $$
  > 
  > 其中，每层卷积层的输出通道数相同，是 $C_{out}$
  > 
  > 整个稠密块，输出的通道数，就是 $C_{in} + C_{out} * N_{conv}$ 
  > 
  > ---
  > 
  > 其中，输出通道数 $C_{out}$ ，被称为增长率，growth_rate, $k$ 

- 过渡块
  
  > 降低特征图的通道数 + 特征图的高/宽减半。
  > 
  > 1x1 卷积：降低通道数
  > 
  > 汇聚层：高 / 宽减半
  > 
  > 起到数据压缩的作用，避免通道数增长过快

- 网络结构
  
  > 7x7 卷积，跟汇聚层，高/宽减半
  > 
  > 跟 4 个`稠密块`，DenseBlock。每个`稠密块`，4 个卷积层，增长率 k=32,
  > 
  > 每个`稠密块`，都跟一个`过渡块`。每个`过渡块`令特征图通道数减半，高/宽减半。其中最后一个稠密块后面，不需要过渡块。
  > 
  > 全局汇聚层，压缩每个通道为一个数值，再展开做全连接。

- DenseNet-121 参数个数
  
  > 7.9M 个参数
  > 
  > 计算过程 [DenseNet_analysis2.ipynb](https://github.com/garrisonz/reproduce/blob/main/DenseNet/DenseNet_analysis2.ipynb)
  > 
  > 网络结构 [DenseNet.png](https://github.com/garrisonz/reproduce/blob/main/DenseNet/DenseNet.png)
