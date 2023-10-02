# Day-17-Paper Reading -- Graph Embedding - 續

## Graph Embedding Techniques
不同 graph embedding 的方法主要的差異在於他們希望保留哪樣的 graph property。

### Matrix Factorization
1. Graph Laplacian Eigenmaps
1. Node Proximity Matrix Factorization

#### Graph Laplacian Eigenmaps

laplacian eigenmaps 的重點概念是希望儘可能地保留節點間的相似度，也就是說，如果兩個節點在原始圖中相似，那麼在嵌入空間中也希望它們的嵌入向量相似。如果它們最後嵌入的結果較遠，那麼就會給予 penalty。
> **objective function**  
> 
> ${y^*} = \arg \min {\sum}_{i \ne j} ({{y_i} - {y_j}){^2}{W_{ij}}}= \arg \min {y^T}Ly$
>> - $y^*$ 最佳嵌入向量
>> - $W_{ij}$ node $i$ 跟 node $j$ 之間的相似程度
>> - $L = D - W$

#### Node Proximity Matrix Factorization
但是也有人直接嘗試分解 proximity matrix，讓節點之間的關係可以用更簡單的方式來表示。

> **objective function**  
> 
> $\textstyle \min \Vert W- Y{Y^c}^T \Vert$

### Deep Learning
1. Random Walk
1. without Random Walk

#### Random Walk
簡單來說就是隨機走訪 graph 中的 node（取樣的概念），然後再把最後的結果丟進去訓練。
- DeepWalk
  - 從 SkipGram 演變而來
  - 使用截斷式隨機遊走，意思就是使用均勻抽樣，直到達到最大長度
- GenVector
- Constrained DeepWalk
- DDRW
- TriDNR
- node2vec
- UPP-SNE
- Planetoid
- NBNE
- DGK
- metapath2vec
- ProxEmbed
- HSNL
- RMNL
- DeepCas
- MRW-MN

#### without Random Walk
沒有使用 random walk 的方法，直接使用深度學習的方法來做。通常會應用像是 autoencoder、deep neural network 或是 CNN 相關的概念。

目前有哪些 Graph Embedding
- SDNE
- DNGR
- SAE
- SCNN
- MoNet
- ChebNet
- GCN
- GNN
- GGS-NNs
- HNE
- DUIF
- ProjE
- TIGraNet

## 參考資料
1. [推荐系统玩家之矩阵分解(Matrix Factorization)的基本方法及其优缺点](https://www.zhihu.com/tardis/zm/art/145120275?source_id=1003)
1. [機器學習_學習筆記系列(74)：拉普拉斯特徵映射(Laplacian Eigenmaps)](https://tomohiroliu22.medium.com/機器學習-學習筆記系列-74-拉普拉斯特徵映射-laplacian-eigenmaps-1a0a5aa04b3c)
1. [降维（二）----Laplacian Eigenmaps](https://blog.csdn.net/jwh_bupt/article/details/8945083)
1. [Laplacian EigenMaps](https://zhuanlan.zhihu.com/p/496040201)
1. [图嵌入（拉普拉斯特征映射Laplacian Eigenmaps）](https://blog.csdn.net/lxx333666/article/details/110497689)
1. [Graph Embedding学习笔记（2）：Laplacian Eigenmaps](https://blog.csdn.net/weixin_34306593/article/details/88749982)
1. [降维总结之Graph Laplacian，Laplacian EM](https://blog.csdn.net/zwlq1314521/article/details/59483135)