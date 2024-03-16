《Transfomers for machine learning A deep dive 》
Introduction



早在1940年，S.McCulloch 和W。pittts使用一个简单的电路“阈值逻辑单元”来仿真大脑的工作。


transfomer的结构在2017年引入，在文章“Attension is all  you need, for sequence to sequence”。它作为使用循环or conv的一种替代。自提出后，很多研究来提升基础transfomer的性能。集中在三点：1.结构修改2.预训练方法3.应用。
修改过的transfomer结构 可以被分为两大类：changes of tran block的安排 changes to the layers that a tran block is made of

Basics and intro
很多nlp和语音识别技术需要处理大量的sequence作为输入，并把它转为特定的输出。传统的方法，如rnn有很多缺点无法完成实际任务。tran成为了克服这些限制最基础的设计 并有着最好的结果。 一开始介绍sequence to sequence和其限制。

本章介绍诸多的building block：如attention、multi-head attention、positional encodings、residual connections and encoder-decoder frameworks.

### encoder-decoder 结构
很多NLP问题，如机器翻译，问题回答和文本总结，把很多序列命名为sequence来作为输入来训练网络。

### sequence to sequence
机器翻译和很多其他的nlp问题产生了好的结果 使用 sequence-to-sequence结构。

#### encoder
输入的句子tokernized into words words映射成特征向量作为encoder的输入。假设输入sequence表达为$x_1,x_T$表示第t个token。embedding 映射将其转换为向量。一个单向RNN网络
#### DEcoder
decoder有encoder的输出，即context变量 given的输出#y_1,,y_T#产生最后的输出。和encoder类似，decoder隐藏状态给出。decoder
#### trianing
decoder预测了每一步的输出token的概率分布
链接 bos和原始输入序列的过程，去除原始的token作为decoder的输入，这个过程称为teacher learning.帮助处理慢的收敛性和不稳定性

#### 基于RNNen-de的问题

changes to an en-decoder 是一个attention层和query，keys和values的映射，是


