[[深度学习基础知识学习]]
传统方法：it doesn't have a way of knowing which pixles are close to each other
CNNs  have properties that provide an effective solution to these problems:
1. they connect neurons , which only correspond to neighboring pixels of the image. redueces  the number of weights,not all neurons are interconnected
2. A CNN use parameter sharing. in other words, a limited number of weights are shared among all neurons in a layer.

The output  of the filter  is a **weighted sum of its inputs** (the activations of the input neurons). Its purpose is to **highlight a specific feature** in the input, for example , an edge or a line. The group of nearby neurons
the neuron takes input only from a limited number of input neurons in its immediate surroundings. This is opposed to [[fully connected]], where the input comes from all neurons.

for each new neuron, we'll **slide** the filter across  the input image and we'll compute its output with each new set of input neurons.
By saying "slide" ,mean the weights of filter don't change  across the image. 
in effect, we'll use the 9 filter weights 来计算所有输出neuron的activations 我们称之为 parameter sharing
两点原因：
1. 减少weights的数量，减少memory footprint，避免过拟合
2. filter highlight特殊的特征。我们可以假设该特征是有用的，不管其在图像的位置，我们保证filter可以用来定位图像的特征

the spatially arranged neurons 被称为depth slices 或者特征图
在卷积层中，bias weight也被所有的neurons shared

a filter highlights a specific feature ，such as edges or lines 
an output slices can recieve input from:
1. a single input slice. the operation is known as **depthwise convolutuon**
2. a single input output slices

一个滤波器宽度$F_w$ 高度$F_h$,输入的深度是$D$,输出的深度是$M$,
$W=(D*F_w*F_h+1)*M$
全连接层是卷积层的一种特例

卷积层中的stride and padding
我们可以slide the filter多个像素，此参数是stride。
larger stride最主要的影响会造成感受野的则更加。一个输出神经元cover了更大的区域，相较输入神经元。 使其可以探测输入更大和更复杂的特征。
stride大于一通常称为stride卷积

$1\times 1$卷积是卷积的特例。bottleneck层

卷积层的后向传播

池化层：同stride一样增加感受野 。不改变深度
max pooling
average pooling
pooling layers由两层来定义 stride 和感受野的大小
一般使用两种，1st是$2\times 2$with stride 2 or $3\times 3$with stride 2
池化层也很经常使用，但我们可以使用更大的stride来达到类似的效果

大多数CNN含有基本的性质：
1. We would typically alternate one or more 卷积层with一个pooling层 。in this way,卷积层可以探测各个level的感受野尺寸。

**提升CNN的性能**
**数据预处理**
1. 数据归一化 feature scaling 把inputs弄到[0,1]之间
2. standard score$x=(x-\mu)/\sigma$

**正则化（避免过拟合）**：regularization is any modification we make to a learning algs that is intended to reduce generalization error but not training error
1. weight decay  添加值到损失函数中 penalize  large network weights 避免网络rely heavily on a few features和这些关联的。 因为当网络工作在多个特征上时，过拟合机率较小
2.  dropout 可以应用在一些网络层的输出，它随机和周期地remove掉网络中地neurons。在一个training的mini-batch里，each neuron有一定概率被随机dropped。这样可以确保没有神经元过度依赖其他神经元，学习到网络中其他有用的东西。

**数据增强**
如果训练集太小，网络会过拟合。数据增强扩大训练集的大小。这些操作有rotation 水平flip、zoom in/out、crop、skew、对比度和亮度增强

**Batch Normalization**： it normalize 每个mini-batch的隐藏层的输出 在卷积层和全连接层都可以使用 加速 使用更高学习率

