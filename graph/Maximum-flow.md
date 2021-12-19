# 最大流问题 (maximum flow problem)

![](image/2021-12-19-14-57-09.png)

左图：

* 边上的权可以看作是能负载的最大容量的流

右图：

* 在不违背原则的情况下，最大流算法的结果 ( 从 `s` 流出的流最大 )

解决问题时两个原则
1. 不违反**边的容量**
2. 保持流守恒

[wiki](https://zh.wikipedia.org/wiki/%E6%9C%80%E5%A4%A7%E6%B5%81%E9%97%AE%E9%A2%98) 详细的说明

## 一个简单的最大流算法
![](image/2021-12-19-14-44-43.png)

下面系列图的第 3 个为 `残余图 - 流图` 的结果

避免直接讨论 `残余图` 是为了防止得到某些坏结果 ( 详见p233 )

![](image/2021-12-19-14-46-01.png)

![](image/2021-12-19-14-46-06.png)

## 优化
体现在找[增长路径 (augmenting path)](https://stackoverflow.com/questions/10397118/what-exactly-is-augmenting-path)的方法上
1. 无权最短路径
2. 赋权最长路径 ( 对 `Dijkstra` 单线修改 )
3. 其他我目前深究不了的算法