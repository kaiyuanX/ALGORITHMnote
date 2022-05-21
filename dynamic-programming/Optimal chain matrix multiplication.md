# 矩阵乘法的顺序安排
$P(n)$ 为 $n$ 个矩阵的可能加括号方法

以下为暴力求解所需次数的递推

![](image/2022-05-10-16-19-25.png)

用假设带入法知 $P(n)=\Omega(2^n)$

**动态规划优化：与 `OptimalBST` 思路一模一样**

## 原理
若 最后一次乘法为 $(A_{left}A_{left+1}\cdots A_i)(A_{i+1}A_{i+2}\cdots A_{right})$

若 $M_{left,right}$ 为从 $left$ 到 $right$ 的最佳乘法次数

$M_{left,right}= min\lbrace M_{left,i}+M_{i+1,right}+c_{left-1}c_{i}c_{right} \rbrace$

## 迭代图
与 `OptimalBST` 一样

## 时间复杂度
$O(n^3)$

## 代码
见 `Dynamic/Optimal chain matrix multiplication`