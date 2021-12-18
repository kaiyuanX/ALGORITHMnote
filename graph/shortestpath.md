# 最短路径 (shortestpath)

## Dijkstra
==简介==

**单源最短路径算法，没有负权。**( 或者说绝大多数 Dijkstra 算法不能有效处理带负权的边 )

基于贪婪

> Dijkstra algorithm is also called single source shortest path algorithm. It is based on greedy technique.

==思想==

利用已经找到的点的最短路去推其他点的最短路

==算法正确性==

易证

==伪代码==

![](image/2021-12-17-17-48-17.png)

==优化==

主要体现在伪代码第二行

1. 普通实现，即遍历整个表得到 `smallest unknown distance vertex`，时间复杂度为 $O(|E|+|V|^2)$
2. 若基于 `Fibonacci heap` 实现则时间复杂度为 $O(|E| + |V|\log |V|)$

---

## Bellman–Ford
==简介==

**能在负权图中正常运行，并判断负圈。**

基于动态规划

[视频](https://www.bilibili.com/video/av48431327/) 04:00

==优化==

用队列优化后：SPFA (Shortest Path Faster Algorithm)

待完善。。。

---

## Floyd
==简介==

**对所有点求最短路径的算法，没有负圈。**

不返回路径本身的细节

==思想==

算法思想与 `Warshell 求传递闭包` 非常相似，或者说是一模一样

`Warshall 算法` 是通过每次加入一个顶点，看把这个顶点作为中间顶点是否能改进传递闭包的矩阵
( 通过这个新加入的顶点作为中间桥梁，使得原来不可达的2个顶点可达，以此逐步向传递闭包逼近 )

`Floyd 算法` 非常类似，通过初试的权重矩阵，每次加入一个顶点，看这个顶点是否能作为中间顶点改变图的权重矩阵
( 加入这个中间顶点后，每两个点之间的最短距离是否减小 )

==复杂度==

时间复杂度：$O(|V|^3)$

当是稠密图时，紧凑的循环让它比用 $|V|$ 次 Dijkstra 算法会更快

当是稀疏图时，用 $|V|$ 次优先队列优化的 Dijkstra 算法会更快

[额外参考](https://www.cnblogs.com/jmzz/archive/2011/07/01/2095158.html)

---