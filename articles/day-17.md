# Day-17-Paper Reading -- Graph Embedding - 續

## Graph Embedding Techniques
The differences between different graph embedding algorithms lie in how they define the graph property to be preserved.

### Matrix Factorization
1. Graph Laplacian Eigenmaps
1. Node Proximity Matrix Factorization


#### Graph Laplacian Eigenmaps
什麼是 Laplacian Matrix？

- $y^*$ 最佳嵌入向量
- $W_{ij}$ node $i$ 跟 node $j$ 之間的相似程度

> **objective function**  
> 
> ${y^*} = \arg \min \mathop{\sum}_{i \ne j} ({{y_i} - {y_j}){^2}{W_{ij}}}$

## 參考資料
1. [推荐系统玩家之矩阵分解(Matrix Factorization)的基本方法及其优缺点](https://www.zhihu.com/tardis/zm/art/145120275?source_id=1003)
1. [機器學習_學習筆記系列(74)：拉普拉斯特徵映射(Laplacian Eigenmaps)](https://tomohiroliu22.medium.com/機器學習-學習筆記系列-74-拉普拉斯特徵映射-laplacian-eigenmaps-1a0a5aa04b3c)
1. [降维（二）----Laplacian Eigenmaps](https://blog.csdn.net/jwh_bupt/article/details/8945083)
1. [Laplacian EigenMaps](https://zhuanlan.zhihu.com/p/496040201)
1. [图嵌入（拉普拉斯特征映射Laplacian Eigenmaps）](https://blog.csdn.net/lxx333666/article/details/110497689)
1. [Graph Embedding学习笔记（2）：Laplacian Eigenmaps](https://blog.csdn.net/weixin_34306593/article/details/88749982)
1. [降维总结之Graph Laplacian，Laplacian EM](https://blog.csdn.net/zwlq1314521/article/details/59483135)