[[矩阵设计]]
rule1:Order the rows such that the top half of H_2^2n are the rows of H − 22 1
rule2:Ordering the third quarter of H22n as the transpose of its second quarter
rule3:Ordering the patterns within each quarter according to the number of blocks they contain

**第k阶需要由第k-1阶来构造**
每一阶有四个group，对于index_k的每一个元素进行下述操作
1. 由rule1构造1st group，在翻折矩阵的行翻折和列翻折的开始补1
2. 由rule1剩下元构造 2rd group  在翻折矩阵的行翻折开始补1 列翻折的开始补-1 
3. 由2rd group转置构造3th group  将step2的完整序列进行前后序列的互换
4. 剩下的元素构成4th group 用完整集合减去上述集合
5. 对each group进行CC排序的操作
 ![[rd1.jpg]]
 ![[rdnum.jpg]]