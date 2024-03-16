a completion network for reconstruction from compressed acquisition

	# 摘要
我们在这里考虑从少数的线性测量重建图像的问题。这个问题有许多生物医学应用，例如计算机断层扫描、磁共振成像和光学显微镜。虽然这个问题早已被压缩感知方法解决了，但现在深度学习方法的效果已经超越了这些方法。然而，理解为什么深度学习方法运行良好仍然是一个悬而未决的问题。在这项研究中，我们提出使用将重建问题理解为 贝叶斯补全问题，其中缺失的测量值是从获得的测量值中估计出来的。从这个角度来看，出现了一个包含完全连接层的网络，该层提供了最佳的线性补全方案。与直接网络相比，该网络需要学习的参数要少得多，并且比纠正伪逆解的图像域网络训练得更快。尽管这项研究侧重于计算光学，但它可能会为具有相似公式的逆问题提供一些见解。

# 引入
单像素成像是计算光学的一种极端配置，其中使用单点探测器来重新覆盖图像 [1]。 这已应用于荧光显微镜 [2]、高光谱成像 [3、4]、弥散断层扫描 [5] 和图像引导手术 [6]。 单像素测量模型从数学上可以理解为图像和一些通过空间光调制器二维函数之间的点积 [7]。 为了限制采集时间，非常需要减少光模式的数量，这会导致欠定的逆问题。

从压缩采集中重建图像，中未知数的数量大于测量的数量，这是一个通用问题，在生物医学成像领域有多种应用（例如，有限角度计算机断层扫描，压缩磁共振成像、计算光学）。 虽然此类问题由压缩感知理论求解，它利用
稀疏先验，最近基于深度学习的研究已经显示出有希望的结果 [8]。 目前投入了很多精力解释和理解为什么这样的逆模型表现良好。 这项研究是朝着这个方向迈出的一小步。 尽管这项研究侧重于计算光学，它可能会为具有类似问题的问题提供一些见解。

在[9]中，作者提出了一种卷积自动编码器用于优于压缩传感方法的单像素成像。 该网络直接映射测量向量到所需的图像，使用全连接层(FCL) 后跟卷积层。 这种架构类似于流形近似（AUTOMAP）网络的自动变换[10]，它已成功地完全应用于磁共振成像。 在这里，我们重点了解 FCL 的行为及其与图像空间学习策略的联系，其中网络后处理近似解，通常由现有算法获得。
# 工作
受 [12] 的启发，我们采用了贝叶斯框架。 从压缩采集重建被解释为一个完成问题，其中丢失的测量必须是估计的。 特别地，我们建议估计缺失的
测量值与获取的测量值的相关性。 对于给定的数据库，我们推导出最佳线性解决方案对于完成问题。 然后，我们将此线性解决方案解释为类 AUTOMAP 网络的 FCL，其中只有训练卷积层。 冻结 FCL 显着减少了要学习的参数数量。
# 压缩成像
$f$定义为需要获取的图像，压缩成像的主要想法是通过硬件来获取$f$的压缩数据，然后通过软件来恢复数据。获取模型可以由
$$m=P_1 f$$
$P_1$sequentially加载到DMD上。通常有Fourier，DCT，小波，Hadamard
# 压缩图像重构
在过去的 10 年里，图像重建通常是通过解决形式的最小化问题来进行的
$$\min _{f} \mathcal{R}(\boldsymbol{f}) \quad \text { such that } \quad \boldsymbol{m}=\boldsymbol{P}_{1} \boldsymbol{f}$$
其中$\mathcal{R}$一般选择$l_2范数$，该问题的闭式解为
$$
\boldsymbol{f}^{*}=\boldsymbol{P}_{1}^{\top}\left[\boldsymbol{P}_{1} \boldsymbol{P}_{1}^{\top}\right]^{-1} \boldsymbol{m}
$$
$\mathcal{R}$的另一种解为全变分范数最近，有人提议学习使用非线性模型重构 f。然后通过迭代算法求解上述问题

最近，有人提议学习使用非线性模型重构
$$
\boldsymbol{f}^{*}=\mathcal{H}(\boldsymbol{m} ; \boldsymbol{\theta})
$$
其中$\mathcal{H}$是

id: 0684572c0e384e75934192866dcea5d6
parent_id: 232e9b3cb92f499a8c66414fe4052682
created_time: 2021-06-07T02:45:58.674Z
updated_time: 2022-01-25T12:22:31.643Z
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
user_created_time: 2021-06-07T02:45:58.674Z
user_updated_time: 2022-01-25T12:22:31.643Z
encryption_cipher_text: 
encryption_applied: 0
markup_language: 1
is_shared: 0
share_id: 
conflict_original_id: 
type_: 1