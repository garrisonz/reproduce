##### VGG

> 使用块结构，令神经网络的结构模块化，更容易设计。

##### VGG 块

- 块结构
  
  > 多个卷积层 + 1 个最大汇聚层
  > 
  > 可指定 VGG 块的输入通道数 $C_{in}$ / 输出通道数 $C_{out}$
  > 
  > 其中，第一个卷积层的的输出通道数是 $C_{out}$ ，后面所有卷积层的输入 / 输出通道数都是 $C_{out}$ 
  > 
  > 每个卷积层后面，都跟一个 ReLU ，提供非线性性

- 特征图的改变
  
  > 卷积层，可改变通道数
  > 
  > 最大汇聚层，将高 / 宽的尺寸，分别减半

##### VGGNet

- 网络结构
  
  > 每经过一个 VGG 块，通道数翻倍，高宽分别减半。
  > 
  > 其中，通道数，增加至 512 后，不再增加。
  > 
  > 展开元素至 1 维度，供全连接层使用
  > 
  > 全连接层，元素个数逐渐减少[4096, 4096, 1000]
  > 
  > 每个全连接层后，都跟一个 `ReLU` ，提供非线性性，再跟一个 `Dropout` ，降低模型容量，减轻过拟合。

- VGG-11 参数个数
  
  > 约 133M 个参数
  > 
  > 计算过程：[VGG_analysis.ipynb](https://github.com/garrisonz/reproduce/blob/main/VGG/VGG_analysis.ipynb) 
  > 
  > ![](https://github.com/garrisonz/reproduce/blob/main/VGG/VGG-11.png?raw=true)
