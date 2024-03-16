[[未训练重构]]
生成模型已经展现了他们在压缩感知问题中从一小部分采样中重构出高分辨图形的能力。这样高的一个压缩率在以稀疏度的手工先验中是不可能的。然而，这些基于深度学习的方法的成功是基于大量的数据集的，然而这些图片在很多领域中是难以获取的，如医学成像。数据标签对于一个分类任务是必要的，参考图像对于一个逆问题是需要的。因此，这样模型的广泛性在很多实际应用中是受限的，因为由于缺少专家的annotator，时间。道德限制，和经济上的原因，是很难来创造这样大的可靠的标签数据。并且，需要指出不是所有的深度学习方法需要标签图像。然而，这样的方法仍然需要大量的干净数据来训练生成模型在预训练模型可以用来解决图像逆问题。对比于5中使用的方法，unnp可以恢复出可信赖的估计当使用一个简单的噪声测量的情况下。

为了减小传统手工先验(suffer from poor discriminative capability)和DL-based的方法(通常需要大的标签数据集，paired datasets for端到端的深度模型的训练)UNNP成为一种有潜力的研究。这种先验被证明是优于传统的手工设计的先验，并且提供了和DL-based 方法相当的表现当结合前向模型的知识并且不需要大量的标签数据集的情况下。更具体地，这些先验假定丰富的图像统计信息可以由随机初始化的CNN来进行随机初始化，随机初始化的网络weights用作重构图像的参数化。

**UNNP弥补了传统手工设计先验（在区分能力上表现不佳）和基于深度学习（DL）的方法（通常需要大规模标记数据集，即成对数据集来端到端训练深度模型）之间的差距**。这些先验已被证明在性能上超过了传统手工设计的先验，并且与基于DL的方法相当，同时在不需要大量标记数据集的情况下融合了前向模型的知识。**具体来说，这些先验假设丰富的图像统计信息被随机初始化的卷积神经网络（CNN）的结构所捕获，其中随机初始化的网络权重作为恢复图像的参数化**。自从UNNP被提出以来，它们已被广泛应用于许多IIPs中。尽管它们取得了显著的成功，但与UNNP相关的文献仍然混乱，给该领域的研究人员带来了显著的挑战。为了填补这一空白，本文提供了一个关于UNNP在IIPs中应用的全面调查。需要注意的是，Ulyanov等人在他们的论文[6]中为UNNP引入了一个不同的术语，称之为深度图像先验（DIP），自那以后，这个替代术语在文献中被广泛使用。然而，用于指代UNNP的术语已经扩展到不仅仅是DIP。我们在表1中提供了用于描述基于未训练神经网络的图像先验的不同替代术语的总结。

IIPs：an introduction
	从观测测量值中重构出未知图像或多维信号被看为一个逆问题，更精确的说，我们考虑逆问题
The algorithms for reconstruction can be divided into three main categories: 1) Linear reconstruction methods, such as differential ghost imaging \cite{ferri_2010_differential} and fast Walsh-Hadamard transform \cite{wang_2016_fast} . 2) Nonlinear reconstruction algorithms, such as compressed sensing algorithms, orthogonal matching pursuit algorithms \cite{pati_1993_orthogonal}, and TVAL3 methods \cite{li_2013_an}. 3) Deep learning reconstruction methods, such as the GIDC method \cite{wang2022far}. While the reconstruction algorithm largely determines the image reconstruction quality of SPI under undersampling conditions, this paper only consider the modulation and encode process here.

The algorithms for reconstruction can be divided into three main categories: 1) Linear reconstruction methods, such as differential ghost imaging \cite{ferri_2010_differential} and fast Walsh-Hadamard transform \cite{wang_2016_fast} . 2) Nonlinear reconstruction algorithms, such as compressed sensing algorithms, orthogonal matching pursuit algorithms \cite{pati_1993_orthogonal}, and TVAL3 methods \cite{li_2013_an}. 3) Deep learning reconstruction methods, such as the GIDC method \cite{wang2022far}. While the reconstruction algorithm largely determines the image reconstruction quality of SPI under undersampling conditions, this paper only consider the modulation and encode process here.


