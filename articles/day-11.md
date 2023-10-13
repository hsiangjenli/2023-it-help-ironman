# Day-11-線上資源

## 開源資料集 - SNAP
目前最有名的公開資料集 [SNAP](https://snap.stanford.edu/data/index.html)、[Open Graph Benchmark](https://ogb.stanford.edu) 是由 Stanford 的教授 Jure Leskovec 所提供。另外也可以到 [Paper With Code - Graph](https://paperswithcode.com/area/graphs) 底下查看各種任務底下的資料集，雖然大部分的資料集在 SNAP 都可以找到。其他在 github 也有人統整一些公開的資料集像是 [benedekrozemberczki/datasets](https://github.com/benedekrozemberczki/datasets)

## 開源程式碼
開源程式碼的部分有很多，像是 NetworkX 這種比較傳統的 graph 算法，或者是比較新的圖神經網路。除了使用 Python 對圖進行操作之外，也要考慮到怎麼樣將圖儲存起來，比較有名的的圖形資料庫有 Neo4j，但是也有其他比較新的圖形資料庫，像是 Memgraph 等等。現在要使用相關的資料庫都可以直接使用 docker 進行部署很方便。

### 視覺化
- [netgraph](https://github.com/paulbrodersen/netgraph)
- [gravis](https://robert-haas.github.io/gravis-docs/index.html)

### 傳統圖算法
NetworkX 有提供隨機生成圖的功能（`erdos_renyi_graph` `watts_strogatz_graph` `barabasi_albert_graph` 等...），另外也提供直接使用 pandas 匯入資料的功能。主要提供的是傳統的圖算法，像是 jaccard_coefficient、pagerank 等等。另外，NetworkX 主要是使用 CPU 進行運算，如果要使用 GPU 加速，可以使用 cuGraph。cuGraph 是由 Nvidia 開發的圖算法，可以使用 GPU 加速，也支援 GNN。

- [NetworkX](https://github.com/networkx/networkx)
- [cuGraph（GPU Support）](https://github.com/rapidsai/cugraph)


### 圖神經網路
- [pyG - pytorch_geometric](https://github.com/pyg-team/pytorch_geometric)
- [DGL](https://github.com/dmlc/dgl)
- [pykeen](https://github.com/pykeen/pykeen)

### Benchmark
- [OGB](https://github.com/snap-stanford/ogb)

### 圖型資料庫
雖然 Neo4j 是最有名的圖型資料庫，但是在開源的部分，其實有很多選擇，像是 Memgraph 等等。
- [Neo4j](https://github.com/neo4j/neo4j)
- [Memgraph](https://github.com/memgraph/memgraph)

## 公開課程/講義
公開課程的部分，Leonid Zhukov 的 Network Science 課程有提供 Youtube 影片可以觀看，會比單看 PTT 上的內容更好理解。

- [Stanford - CS224W: Machine Learning with Graphs](https://web.stanford.edu/class/cs224w/)
- [Leonid Zhukov - Network Science](http://www.leonidzhukov.net/hse/2021/networks/index.html)
   - [Youtube](https://www.youtube.com/c/LeonidZhukov)
- [Albert-László Barabási - Network Science](http://networksciencebook.com)
- [Antonio Longa - GNN](https://www.youtube.com/@94longa2112/videos)
- [Social Network Analysis for Computer Scientists](https://liacs.leidenuniv.nl/~takesfw/SNACS/)

## 參考用書
- [Practical Social Network Analysis with Python](https://link.springer.com/book/10.1007/978-3-319-96746-2)