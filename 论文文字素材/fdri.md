[[逆矩阵]]理论

FDRI是一种压缩成像中基于测量矩阵归一化逆的重构方法。问题的解通过最小化解和一系列空间滤波器卷积的范数进行正则化。问题的解需要矩阵的逆来获得正则化的逆矩阵。一旦矩阵被存储到空间中，重构过程只需要单步的矩阵相乘计算，这在重构时间上会明显优于l1最小化的方法。同时在重构质量上表现相当。

# 理论
该方法解决的是欠采样测量的图像重构问题。单像素成像的数学模型可以简单写成$y=Mx$，其中$x$是向量化的图像，$M$是向量化散斑作为行的测量矩阵。我们考虑图形$x$和$h$卷积的$l_2$范数的最小化而不是$l_1$范数。
# 引入
在欠采样条件下，重构过程 压缩测量通常是歧义且需要优化方法。压缩感知的框架提供了较优的重构质量，基于稀疏图像的$l_1$范数最小化的方法。然而，正则化的单步重构方法用来解决欠定逆问题明显更快，至少对于中等尺寸的测量。

id: 37f588f4b1c14f8c8bf3686508e8210b
parent_id: e39441788f074eb4a2991e892f26f031
created_time: 2021-06-03T07:28:58.929Z
updated_time: 2021-06-03T08:19:04.824Z
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
user_created_time: 2021-06-03T07:28:58.929Z
user_updated_time: 2021-06-03T08:19:04.824Z
encryption_cipher_text: 
encryption_applied: 0
markup_language: 1
is_shared: 0
type_: 1