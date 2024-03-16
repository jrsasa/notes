最近。Ulyanov等人提出深度图像先验（DIP）框架，使用一个未训练神经网络作为图像处理任务如去躁、修复和超分辨。它们证明一个正确设计的生成器网络结构本身会有一个implicit的bias towards 自然图像，因此可以用来解决欠定逆问题。
DIP的优势是一个生成器网络可以被用来，因此消除了数千个labeled data.

它使用一个未训练

首先，我们关联H和I通过DGI来得到一个rough重构。其次，我们feedDGI重构结果到一个随机初始化的神经网络中。第三，我们take神经网络的输出作为高质量GI图像的估计并用它来计算桶探测信号，最后，我们更新神经网络的权重来最小化桶探测


```python
# Create two variables.
weights = tf.Variable(tf.random_normal([784, 200], stddev=0.35),
                      name="weights")
biases = tf.Variable(tf.zeros([200]), name="biases")
...
# Add an op to initialize the variables.
init_op = tf.global_variables_initializer()

# Later, when launching the model
with tf.Session() as sess:
  # Run the init operation.
  sess.run(init_op)
  ...
  # Use the model
  ...
```
介绍local、global初始化和checkpoint https://chromium.googlesource.com/external/github.com/tensorflow/tensorflow/+/r0.12/tensorflow/g3doc/how_tos/variables/index.md