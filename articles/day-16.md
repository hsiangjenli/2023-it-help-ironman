# Day-16-Paper Reading -- Graph Embedding - 續

## Graph Embedding Output

跟 input 不同的是，embedding output 是 task driven，所以在什麼任務底下適合的 embedding 方式不一定適合其他的任務。
### Node Embedding
node embedding 是指將 node 轉換到一個低維度的向量空間裡。不同 embedding 的方法下對兩個 node 的『closeness』定義不同。

### Edge Embedding
edge embedding 跟 node embedding 類似，目標是將 edge 轉換到一個低維度的向量空間裡。

但是它有一些比較特別的應用場景，例如：knowledge graph embedding。因為需要兩個節點才能成一條邊，所以 edge embedding 同時會考慮到 node 跟 edge 的資訊，目標就是將三位元組 <head, relation, tail> 映射到低維度的向量中，同時保留住 head 跟 tail 之間的 relation。所以當只有只有 head 跟 tail 的時候就可以用來預測這兩個 node 之間的 relation。

困難的點在於：
1. 怎麼去定義 edge 的 closeness，因為邊的組成是由兩個 node 組成，所以 closeness 的定義就會比單純的 node embedding 複雜
1. edge 是有方向性的，所以 closeness 也會因為 node 的順序不同而有所不同
1. 不像 node embedding，edge embedding 要考量的資訊更多，像是 edge 的方向性、權重等等，這都讓 edge embedding 變得更加困難

### Hybrid Embedding
同時將 graph 不同的 components，例如：node、edge、community 等等。

1. Substructure Embedding
1. Community Embedding

### Whole Graph Embedding
把整個 graph 轉換到一個低維度的向量空間裡，這種 embedding 的方法通常只會使用在比較小的 graph 上，像是 protein、molecule。

-  hierarchical graph embedding framework
   - 用來評斷這個 embedding 的好壞
   - 像是 embedding 的時間、保留了多少的資訊