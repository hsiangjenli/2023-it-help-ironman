# Day-29-Paper Reading -- A Survey on Embedding Dynamic Graphs

```python
@article{barros2021survey,
  title={A survey on embedding dynamic graphs},
  author={Barros, Claudio DT and Mendon{\c{c}}a, Matheus RF and Vieira, Alex B and Ziviani, Artur},
  journal={ACM Computing Surveys (CSUR)},
  volume={55},
  number={1},
  pages={1--37},
  year={2021},
  publisher={ACM New York, NY}
}
```

![](./../image/image-21.png)

在 Day-03 的時候有稍微提到 Dynamic Graph，但是關於 Dynamic Graph 的研究相對於其他還是少了些，開源的專案基本都 focus 在 static graph 上，所以這邊就來看一下這篇論文，來稍微補一下這塊的知識。

## Abstract
However, many real-world networks present dynamic behavior, including topological evolution, feature evolution, and diffusion.

such as time-domain modeling, temporal features to be captured, and the temporal granularity to be embedded. 

discussing its fundamentals and the recent advances developed so far

formal definition of dynamic graph embedding, focusing on the problem setting and introducing a novel taxonomy for dynamic graph embedding input and output.

## Introduction
Embedding graphs in low-dimensional vector spaces have been applied to extract features from networks and encoding topological and semantic information, and many researchers have been using these network representation learning approaches for several applications, including node classification and clustering, link prediction, and network visualization

目前的研究主要都是針對 static graph，簡單來說就是只針對一個固定的時間點（graph snapshot）做 embedding。

但是很多真實世界的網路都具有動態行為，如果強制把這些特性忽略掉，可能會導致 embedding 的結果不夠準確。

### The Challenge of Dynamic Graph Embedding
1. 使用哪種時域建模型
   - discrete time
   - continuous time
1. 要捕捉哪些行為特徵
1. which temporal granularity will be represented in the vector space
   - 在向量空間中要如何表示時間的精細程度

## FUNDAMENTALS BEHIND THE EMBEDDING OF DYNAMIC GRAPHS

### Graphs and Static Graph Embedding
這部分先前就提過很多次，因為不是我閱讀的重點，所以就不多做介紹了。

### Dynamic Graphs

Notaion（1）
- Dynamic Graph：![](https://dl.acm.org/cms/asset/399ffb49-3474-4cb6-bd88-8969f87bcf56/3483595-inline26.gif)
- 一系列隨時間變化的節點集合：![](https://dl.acm.org/cms/asset/677bebd4-5af7-4472-a3f9-1ee73b54c8f5/3483595-inline27.gif)
- 一系列隨時間變化的邊集合：![](https://dl.acm.org/cms/asset/c314a232-6d8d-4eac-bfbe-80d18ddfbe68/3483595-inline28.gif)
- Graph Snapshot：![](https://dl.acm.org/cms/asset/a1e8d180-d282-4b78-bf3c-01a0a89fed7a/3483595-inline31.gif)

Notaion（2）
- Dynamic Graph：![](https://dl.acm.org/cms/asset/da3c6d60-994b-4145-8c87-29affe8d007a/3483595-inline38.gif)
- 表示特定時間點上節點 $\mathcal{v}$ 是否存在 $\rho_{\mathcal{v}} : V \times \mathcal{T} \rightarrow \lbrace0, 1 \rbrace$
- 表示特定時間點上節點 $\mathcal{e}$ 是否存在 $\rho_{\mathcal{e}}: V \times \mathcal{T} \rightarrow \lbrace 0, 1 \rbrace$

### Dynamic Graph Modeling
modeling 的方式又分成 discrete time 和 continuous time。

#### Graph Snapshots
簡單來說就是在不同時間點建立 static graph，然後再把這些 static graph 組合起來。

#### Difference Network Models
重點是記錄網絡的拓撲結構（adjacency matrix）隨時間變化的情況，重點是在於邊的變化，而節點的新增或刪除就不會被記錄下來（意思是它的維度只能是一個固定的 adjacency matrix ）。

#### Continuous-time Network Models
像是紀錄下來的邊是有 timestamp，或是使用 link stream 來記錄節點隨著時間變化之間的互動產生的改變。

### Temporal Point Processes on Graphs

temporal point process 可以被表示成 counting process，紀錄在 t 之前所發生的事件數量，可以用來模擬連續時間中發生的順序非同步離散事件。

中間太多內容了先跳過，先講有哪些模型可以用來建模。

### Dynamic Behaviors


> ![](https://dl.acm.org/cms/asset/842c7957-4a32-4387-88cd-9cc4b50f0870/csur5501-10-f06.jpg)
> 
> 圖片來源：[A Survey on Embedding Dynamic Graphs](https://dl.acm.org/doi/full/10.1145/3483595)

## TECHNIQUES FOR THE EMBEDDING OF DYNAMIC GRAPHS
> ![](https://dl.acm.org/cms/asset/cae7c867-f353-4e73-b4a2-74a0070ff7f5/csur5501-10-f07.jpg)  
> 
> 圖片來源：[A Survey on Embedding Dynamic Graphs](https://dl.acm.org/doi/full/10.1145/3483595)

看起來 Dynamic Graph Embedding 的方法跟 Static Graph Embedding 的方法差不多。