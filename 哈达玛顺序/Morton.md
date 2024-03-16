[[矩阵设计]]
构造$\Omega\_M$的整个过程以伪代码的形式在算法中加以描述，首先，我们根据Z-order曲线在二维空间中的遍历顺序给出 对应的空间坐标，根据空间坐标在index 矩阵$I$中的值append到$\Omega\_M$中，直到$\Omega\_M$中有M个元素

下面是最快构造Morton的方式
\| \`\`\`

    clear;clc;
    H=[];
    matrix_size=64;
    N=log2(matrix_size);
    H_64=walsh(64);
    for s=0:4095
        [j,i]=reverseZOrder(s, matrix_size);
        sq=strcat(kthOrderGrayCode(i, N), kthOrderGrayCode(j, N));
        idx=bin2dec(reverse(sq))+1;
        O1(s+1)=idx;
        H(s+1,:)=reshape(H_64(:,i+1)*H_64(j+1,:),[1,4096]);
    end

这和频域下该点取1的构造是一样的,这种方式可以运用到dct fourier的构造，
|`time=cputime;
H=[];
matrix_size=64;
N=log2(matrix_size);
invtransform=@(v)ifwht((ifwht(v).')).';
for s=0:4095     [i,j]=reverseZOrder(s, matrix_size);
    sq=strcat(kthOrderGrayCode(j, N), kthOrderGrayCode(i, N));
    idx=bin2dec(reverse(sq))+1;
    O1(s+1)=idx;
    I=zeros(64);
    I(i+1,j+1)=1;
    P=invtransform(I)';
    H(s+1,:)=reshape(P,[1,4096]);
end`

以下是一维的构造
|\`\`\`

    %     I=zeros(4096,1);
    %     I(idx)=1;
    %     h=ifwht(I,4096,'hadamard');
    %     H=[H;h'];

以上三种构造方式等价，应该是第一种方式最快。（可以做一个对比）

下面将自然序下index 转到（i，j）下
|\`\`\`
function \[i, j] = idxToIJ(idx, N)
% 将 idx 减1然后转换为二进制字符串
binStr = dec2bin(idx-1, 2\*N);

    % 反转字符串
    reversedStr = reverse(binStr);

    % 分割字符串
    iGrayCode = reversedStr(1:N);
    jGrayCode = reversedStr(N+1:end);

    % 将 Gray Code 转换回原始数字
    i = grayToBinary(iGrayCode) + 1;
    j = grayToBinary(jGrayCode) + 1;

end

function num = grayToBinary(grayCode)
% 将 Gray Code 转换为二进制数
num = 0;
binNum = bin2dec(grayCode);
for k = floor(log2(binNum)):-1:0
num = bitxor(num, bitshift(binNum, -k));
end
end\`\`\`
是逆过程

最大的发现是是russian doll和origami都呈方形的分布
![](file:///C:\Users\zd22\AppData\Local\Temp\ConnectorClipboard4800675644742260857/image17013517723480.png)

在本文中，测量矩阵使用的是Hadamard matrix

使用这样的矩阵\mathbf{p}来记录2D Hamard basis毫无疑问是麻烦的，下面我们使用包含original natural ordered number 来为p矩阵的每一个元素做标记。这样的好处是the index facilitates the use of FWHT during pattern generation and spectral cube reconstruction.

从表中的数据我们可以得出结论：HFWHT的重构时间在各个空间分辨率都明显优于DGI,FDRI和TVAL3，在都使用"Morton" sampling strategy时，HFWHT对于spectral cube重构质量也不逊色于压缩感知算法，虽然我们没有引入一些最新的深度学习算法作为参考。但HFWHT的简单适用性是明显高于这些需要大量数据和GPU训练的深度学习算法的

我写efficient hd的排序

写完再写dct的排序(fourier排序是否需要)
