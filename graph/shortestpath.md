# 最短路径 (shortestpath)

## Dijkstra
Dijkstra algorithm is also called single source shortest path algorithm. It is based on greedy technique.

**思想**：利用已经找到的点的最短路去推其他点的最短路

**算法正确性**：易证

**伪代码**

![](image/2021-12-17-17-48-17.png)

优化主要体现在伪代码第二行

1. 普通实现，即遍历整个表得到 `smallest unknown distance vertex`，时间复杂度为 $O(V^2)$
2. 若基于 `Fibonacci heap` 实现则时间复杂度为 $O(E + VlogV)$

## Bellman–Ford
能在负权图中正常运行，并判断负圈。基于动态规划

队列优化：SPFA (Shortest Path Faster Algorithm)

[视频](https://www.bilibili.com/video/av48431327/) 04:00

待完善。。。