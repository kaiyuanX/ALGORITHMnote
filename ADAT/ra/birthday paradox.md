# 生日悖论

一屋子多少人才能使其至少两人同时生日的机会到 50%

1. 一年 $n = 365$ 天
2. 每人每天生日的概率一样

假设总共 $k$ 人，$k$ 个人生日都不一样的概率 : $P=\displaystyle\frac{A_n^k}{n^k}$

题意得出不等式

$\implies1- P > \displaystyle\frac{1}{2}$

$\implies 1 \cdot (1-\frac{1}{n})(1-\frac{2}{n}) \cdots (1-\frac{k-1}{n})<\frac{1}{2} $

见 `CLRS 74`

## 采用指示器变量的一个分析

通过期望

![](image/2022-03-30-17-54-34.png)

两种方法准确数目不同

但在渐进阶数上都是 $\Theta(\sqrt[]{n})$