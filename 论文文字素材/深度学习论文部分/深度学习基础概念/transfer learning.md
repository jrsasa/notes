[[深度学习基本概念]]solve a real ML problem with limited resources?
应用现有的训练的ML model到新的相关的问题

we can do this by removing 一个现存的预训练的网络 最后的全连接层(或者全部的全连接层),replace with另一个层

我们仍需train the new layer with new layer with data related to the new task
我们有两个选项:
1. 使用网络的原有部分作为特征提取,仅训练新的层 
 feed the network a training batch of the new data and propogate it 来看网络的输出.
 但在**反向传播阶段,我们lock the weights of the  original net仅仅更新 新层的weights**
 这是一种推荐的方法,当我们遇到新问题训练集极其有限 当locking网络的大部分参数,我们可以避免在新数据上的过拟合
2. fine tuning整个网络 训练整个网络 我们也可以lock第一层的一些weights idea here是最初始的层探测general的特征,而并不related to specific task. 当有足够数据时,我们可以使用此方法因为无需担心过拟合

迁移学习 coding
