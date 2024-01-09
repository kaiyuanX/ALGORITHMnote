# Eval

==描述==

求递推关系 $C_n = \displaystyle\frac{2}{n}  \cdot \displaystyle\sum_{0}^{n-1}C_i + n $

==递归树==

![](image/2024-01-02-20-46-57.png)

==DP==

1. 记录 $C_i$

2. 记录 $S_i$，即 $\displaystyle\sum_{0}^{i-1}$