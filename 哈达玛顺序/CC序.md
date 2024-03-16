[[矩阵设计]]
**定义**：pattern的connected domain按升序排序 [[SE序]]是一维连通域个数

传统上是通过SE序和经验公式来实现
![[ccseJPG.JPG]]
现有方法：统计pattern的行向量的cd_1记为roc，统计pattern的列向量的cd_1个数，记为coc，
$cd_2=roc\times coc$
行向量的sign change个数时，使用二进制数列后半元素
列向量的sign change个数时，使用二进制数列前半元素
计算cd_2后升序排序
