[[深度学习基本概念]]我们会讨论最近popular的网络结构

在VGG之前,leNet-5和alexnet,initial网络的卷积层 使用filters含有大的感受野 如7x7
并且这些网络有交替的单个卷积和池化层.
VGG的作者观察到一个大filter的卷积层可以替代为 stack of 两个或多个含有小filter的卷积层.例如. replace 一个5x5的卷积层位两个3x3的层.有如下优势
1. the last of the stacked layers的神经元含有单层with 大filter 含有相同的感受野
2. stacked layers的weights和operations的数量更少相较于一个大的filter size层.
如 我们想replace一个5x5的层位两个3x3层. 效率提升
3. stacking multiple layers让decision function更discriminative

VGGnet的深度增加,卷积层的width也同时增加 VGG的weights过大,memory inefficiet
但它仍是一个pooular和straightforward的网络结构, 之后添加BN对其有一定的提升

keras和torch都可以加载预训练的结构
