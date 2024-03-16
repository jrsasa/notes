[[深度学习重构]]

重构时间随着照明散斑数目的增加而大幅增加 很多方法被用来减少获取时间，

人们需要把SPI看成一个误差减小的问题。而传统DGI利用了照明散斑和测量的关联信息。到那时重构质量相较迭代方法较差。非线性优化方法。

GIDL提出了一种全连接的网路来从对应的CS测量中重构图像。

我们提出了一种基于GAN网络的重构技术适用于SPI。我们的目标在于通过generative modelling 重构过程来重构Images。总而言之，一个GAN网络由两部分构成。一个生成网络产生假的图片和一个判别网络学习分辨虚假和真实的图片。在我们的装置中，generator尝试从噪声输入中重构原始信号。discriminator将重构图片看作假图片 通过最小化一个精心设计的loss函数，我们的重构网络具有从噪声图片中学习有用和鲁棒表达来产生清晰重构的能力。另外，我们的结果表明含有跳过连接提升了训练经验和重构性能。

和别的方法的差别在于，SPI-GAN取得了显著的PSNR和SSIM的提升。另外，我们的方法展现了在较高测量噪声上的鲁棒性。我们的工作总结如下几点：
- 设计了一个新的基于深度学习的重构框架来解决SPI中高质量和快速图像重构的问题。我们表明更合适的结构和目标函数的选择会有一个更好的重构
- 由于快速图像恢复，我们的方法也适合于单像素视频应用的场景。我们通过在一个高帧频率下大数据集重构视频证明了这点
- 不同于其他DL-based的重构，SPI-GAN展现了在完全unseen datasets上更好generalization能力，这在很多实用场景更有用。为了证明这点，我们在STL-10训练集上训练网络然后在6种完全不同的未见测试集上测试了性能

共轭梯度法是一种迭代算法，它将图像重构作为一个二次最小化问题。最小化问题使用梯度下降法进行计算。目标是最小化Loss函数通过使用loss梯度来迭代更新重构图像。在CGD中，这些梯度彼此是互相共轭的。由于该原因，共轭梯度法相较梯度下降收敛更快。

交替投影法基于空间频谱的理论。基于稀疏的方法

在不同的成像技术中，深度学习被用来解决恢复图像的逆问题。例如，DL被用来在数字holography，散射介质成像，无透镜成像和荧光生命成像中。不仅于此，最近DL-based的方法在SPI恢复图像中展现了巨大的成功。在大多数情况下，这些方法相较传统迭代方法更好更快。例如，GIDL在重构中使用一个全连接的网络。接着，一个更合适的基于卷积的神经网络的方法被在39中被介绍，被称为DLGI，这可以成功的重构简单的手写体的简单图像。另一个基于深度学习的方法，叫做deepghost提出一种基于autoencoder的结构来从欠采样测量中恢复图像。deepghost基于去噪操作的原理并展现了promising的结果

GAN的应用
最近这些年，GAN被在很多

id: 13bdae31a3484a929fe214317e540e51
parent_id: 232e9b3cb92f499a8c66414fe4052682
created_time: 2021-07-09T13:24:08.792Z
updated_time: 2021-07-10T03:12:58.140Z
is_conflict: 0
latitude: 0.00000000
longitude: 0.00000000
altitude: 0.0000
author: 
source_url: 
is_todo: 0
todo_due: 0
todo_completed: 0
source: joplin-desktop
source_application: net.cozic.joplin-desktop
application_data: 
order: 0
user_created_time: 2021-07-09T13:24:08.792Z
user_updated_time: 2021-07-10T03:12:58.140Z
encryption_cipher_text: 
encryption_applied: 0
markup_language: 1
is_shared: 0
type_: 1