# Day-20-Paper Reading -- Graph Embedding - 續

## Graph Embedding Techniques

### Generative Model
generative model 可以藉由輸入特定的特徵和類別標籤分佈當作參數。

#### Embed Graph Into The Latent Semantic Space
重點在於把 node 映射到 semantic space 的時候，它們之間的距離可以解釋他們在 graph structure 中的關係。

#### Incorporate Latent Semantics for Graph Embedding
這裡的假設是，如果兩個 node 的語意是相近的，那麼他們被 embedded 的時候，他們之間的距離也會相近。

## Applications
- node related applications
- edge related applications
- graph related applications
- other applications

### Node Related Applications
- node classification  
  越像的 node 越應該要有相同的 label
- node clustering  
  非監督式學習，將相似的 node 分到同一個 cluster，embedding 之後，可以直接使用傳統的 clustering algorithm 來做
- node recommendation/retrieval/ranking  
  根據特定的標準，找出跟這個 node top-k 相似的 node

### Edge Related Applications
- link prediction
- triplet classification  
  這是屬於 knowledge graph 的應用，這裡的 triplet 是指 <head, relation, tail>，這裡要做的事情是 classify 這個沒見過的 triplet 是否正確。

### Graph Related Applications
- graph classification  
  graph classification 是指將整個 graph label 成某一個類別，意思是 graph 就是最小單位，像是化合物、有機分子、蛋白質等等。
- visualization

### Other Applications
- knowledge graph  
  從文字中抽取出來的知識，可以被轉換成 knowledge graph
- multimedia network  
- information propagation（資訊傳播）
- social network alignment  
  預測兩個不同社群網路中的 node 是否是相同的使用者所擁有