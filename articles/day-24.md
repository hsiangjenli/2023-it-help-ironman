# Day-24-pyG 的 `nn.Module` 中的 Pooling Layers 用處

![](../image/image-51.png)
> 圖片來源：[Graph Pooling for Graph Neural Networks: Progress, Challenges, and Opportunities](https://arxiv.org/pdf/2204.07321.pdf)

## 到底什麼是 graph pooling？

其實 graph pooling 跟 CNN 中的 pooling 一樣，簡單來說就是對原始的 graph 做 downsampling。

BTW，另外還有一個很容易跟 graph pooling 搞混（類似）的名詞叫做，graph sparsification（稀疏化）。但這兩個名詞究竟有什麼差別，我也不是很確定。

### **sparsification**  
根據這篇 [Graph Summarization Methods and Applications: A Survey](https://dl.acm.org/doi/pdf/10.1145/3186727)，感覺 sparsification 的假設是把「不重要的」節點刪掉也不會對結構造成太大的影響。（所以可能在研究什麼叫做/定義不重要的節點（雜訊）....嗎？？？
> **Simplification or sparsification based**
These methods streamline an input graph by removing less **“important”** nodes or edges, resulting in a sparsified graph.

### **pooling**  
而 pooling 的重點應該在研究有沒有一種方法可以在把 graph downsampling 後「維持原始的結構」。（所以就算是雜訊，也跟著保留下來了
> ![](../image/image-52.png)
>
> 參考資料：[Graph Pooling for Graph Neural Networks: Progress, Challenges, and Opportunities](https://arxiv.org/pdf/2204.07321.pdf)

## 什麼時候會用到 graph pooling？

通常在什麼樣的 task 中會用到 graph pooling？
- Node-level tasks  
  - node classification
  - node clustering 
- Graph-level tasks  
  - graph classification
  - graph regression
  - graph reconstruction
  - graph generation 

## Pooling 的種類
- Flat Pooling
- Hierarchical Pooling
- Other Pooling

### Flat Pooling
又稱作「graph readout operation」。大多數的 flat pooling 都是對 graph 中的 node 做 average 或 sum。

flat pooling 的要求：
1. 即使輸入的 graph 大小不同，輸出的大小仍須一致
1. 當輸入 graph 的節點順序變動時，輸出要保持不變

### Hierarchical Pooling
通過將 graph coarsening（粗糙化）成較小尺寸的 graph，以保留具有 hierarchical structure 的資訊。

Hierarchical Pooling 的方法分成兩種：
- Node Clustering Pooling (time-and space-consuming)
- Node Drop Pooling  (selects a subset of nodes from the original graph to construct a coarsened graph)
  
### Other Pooling
- EdgePool
- HyperDrop

## Reference
- [GNN中的Graph Pooling](https://blog.csdn.net/leviopku/article/details/106949616)
- [Graph Pooling for Graph Neural Networks: Progress, Challenges, and Opportunities](https://arxiv.org/pdf/2204.07321.pdf)
- [Graph Summarization Methods and Applications: A Survey](https://dl.acm.org/doi/pdf/10.1145/3186727)

```
@article{liu2018graph,
  title={Graph summarization methods and applications: A survey},
  author={Liu, Yike and Safavi, Tara and Dighe, Abhilash and Koutra, Danai},
  journal={ACM computing surveys (CSUR)},
  volume={51},
  number={3},
  pages={1--34},
  year={2018},
  publisher={ACM New York, NY, USA}
}
```

```
@article{liu2022graph,
  title={Graph pooling for graph neural networks: Progress, challenges, and opportunities},
  author={Liu, Chuang and Zhan, Yibing and Wu, Jia and Li, Chang and Du, Bo and Hu, Wenbin and Liu, Tongliang and Tao, Dacheng},
  journal={arXiv preprint arXiv:2204.07321},
  year={2022}
}
```