# 图论算法

## 一些概念
边(edge)，点(vertex)，权，路径，路径的长，环(圈)，连通性等基本术语详见**离散数学**

## 图的表示

① 稠密的

邻接矩阵 ( 二维数组 )

对于每条边 $(u,w)$ , 我们置 $A[u][w]=x$

空间需求为 $O({|V|}^2)$

② 稀疏的

邻接表

![](image/2021-12-15-10-49-34.png)

---