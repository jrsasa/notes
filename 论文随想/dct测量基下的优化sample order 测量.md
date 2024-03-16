
![[Pasted image 20231222181347.png]]

## 文中的一些内容：
单像素成像（SPI）在探测器阵列成本高或无法使用时的优越性。它强调采样顺序、采样比率、噪声以及变换类型对重建图像质量的影响。文中比较了在噪声存在的情况下，使用哈达玛变换（HT）和离散余弦变换（DCT）进行的单像素成像的性能。每次测量中增加图像信息与增加噪声之间的平衡导致了重建图像质量的最佳测量次数。此外，**与HT相比，DCT在较少的测量下展示了更高的图像质量**。然后，文章展示了使用最优采样策略的SPI在一系列图像和实验室实验中的应用，并提出了一种质量控制技术，这一技术得到了实际实验的验证。这些结果表明了一种实用的SPI方法，旨在提高速度并实现尽可能高的图像质量。

目前用于欠采样的正交变换通常包括傅里叶变换（FT）和哈达玛变换（HT）。张等人已经比较了HT和FT19。对于大多数实际图像，由于更多的信号能量集中在低频模式上，FT单像素成像（FT-SPI）对于欠采样方法来说比HT单像素成像（HT-SPI）更有效。FT生成复数系数，这导致测量次数增加了一倍。FT的图像质量以大幅增加的测量时间为代价，从而破坏了欠采样的优势。** 相比之下，离散余弦变换（DCT）作为FT的替代选项，也被引入到SPI中。类似于HT，DCT生成实数系数，显著减少了测量次数。对于真实应用来说，对于真实应用来说，比较HT和DCT在SPI中的图像质量、抗噪声能力以及测量效率变得非常重要。**

![[Pasted image 20231222182210.png]]
从图中可以看出在相同采样数下dct重构的性能是优于dct的。
dct在低采样下可能是优于ht的
## sample order 的影响
在SPI中这样的对于sample order 的分析主要集中在ht域内，如cake cutting排序，russian doll 排序，origami排序。这些优化的方式是基于ht变换的binary 特性，是在空域下分析其二维几何性质之后进行排序。如cake cutting排序分析其联通域个数之后对ht的测量基进行升序排序。origami排序需要对每一组内的pattern进行翻折的运算。**很明显，这些空域下的sample order优化方法无法应用到dct域和ft域**。因为传统是用1D的index vector来记录这些优化顺。现在我们用2D的index matrix来记录这些sample order. 然后将其和zigzag，snake这些频域的scanning path和之前的 顺序进行比较。
![[Pasted image 20231222190342.png]]
可以看到gcs和cc的采样性能是十分接近的，但是是否在dct和ft下是否也是这样需要进一步验证。

1.构建cc og rd的2d index matrix 因为这是在频域下的一个分布
function [i, j] = idxToIJ(idx, N)
    % 将 idx 减1然后转换为二进制字符串
    binStr = dec2bin(idx-1, 2*N);
    
    % 反转字符串
    reversedStr = reverse(binStr);
    
    % 分割字符串
    iGrayCode = reversedStr(1:N);
    jGrayCode = reversedStr(N+1:end);
    
    % 将 Gray Code 转换回原始数字
    i = grayToBinary(iGrayCode) + 1;
    j = grayToBinary(jGrayCode) + 1;
end
需要将原先构造的idx 通过这个函数变回gray code sequence下的二维坐标

利用这些排序到dct域和 fourier域进行计算得到相较更优的 首先是高分辨率成像的一个条件 高分辨成像 低采样的一个背景
哈达玛程序的低采样方法被广泛和系统的研究但是在别的采样基下 并没有很多演技 然后是哈达玛和dct采样基下的对比 说明一点dct采样的一些优势
为什么样采用dct基 应该是低采样下效果更好的 

影响SPI的质量因素众多，sampling ordr，sampling ratio，noise and type of transforms影响了重构图像的质量。 比较了hadamard transform和dct下的表现

![[Pasted image 20231222194235.png]]