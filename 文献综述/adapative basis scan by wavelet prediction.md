SPI中自适应的获取 ：利用之前获取的测量值来决定 后面的SLM pattterns，获取新的这个测量值。特别地，adapative basis scan schemes是powerful的，因为测量数可以大幅减少，从而可以实现快速的重构。
本章中，我们介绍了adapative basis scan by wavelet preidiction。
## intro
在大多数ABS 方法里，小波基常使用，因为大多数图片在小波域里有稀疏的表示。并且存在快速的逆变换算法来重构图像。这也是小波基一直在压缩算法，如JPEG2000中重要的原因。在第二节提出的基于小波的ABS主要有两大缺点：
1. 这些技术使用的是thresholding，是image dependent的，因此算法不易tune
2. 考虑使用的小波。实验中进行采样的小波基使用的是Haar小波基，而这并不一定是获取最佳压缩比的小波

我们提出完整的ABS-WP的框架。我们的方法有两个特征：
1. 我们report一个无threshold-free的prediction strategy 基于非线性的小波近似。
2. 使用任意desired的小波基的可能性。
我们表明haar小波基之外的小波基可以提供一个更好的图像质量。

to begin with， 小波变换 detailed，接着是acquisition和prediction strategies。conditions 实验装置 are reported. 和simulated和实验 acquisition are performed。ABS-WP 和现有的CS框架被compared和其他的ABS strategy。
## wavelet transform
wavelet transform是powerful和popular tool。此变换allows the signal to be interpreted as a superposition of oscillating functions called wavelets，在时域和频域localized。
我们对2D图像的wavelet transform with dyadic wavelets感兴趣，我们的图像f is considered as a 一个向量。N是2的power。在本节，小波分解is described， 通过filter banks获取不同小波稀疏地对应公式。notation的简化 is giving next。小波变换的非线性化近似is shown to lead to good image quality with few coefficients
### 小波分解

