# Day-18-Paper Reading -- Graph Embedding - 續

## Graph Embedding Techniques

### Edge Reconstruction Based Optimization
- Maximizing Edge Reconstruction Probability
- Minimizing Distance-Based Loss
- Minimizing Margin-Based Ranking Loss

#### Maximizing Edge Reconstruction Probability
最大化重建邊的機率

好的 embedding 方法是可以在 input graph 重建出原本的 edge（？）
##### First-order Proximity
- ${p^{(1)}}({v_i},{v_j})$ ---> $v_{i}$ 跟 $v_{j}$ 之間的 first-order proximity，可以藉由 joint probability 計算出來
- 用微觀一點的角度來看，就是要最大化任兩點連接的機率
  - ${p^{(1)}}({v_i},{v_j}) = \frac{1}{{1 + \exp (- {y_i}^T{y_j})}}$ 
- 但因為最佳化的目標是所有節點，所以要把它們都加總起來
  - $\mathcal{O}_{max}^{(1)} = \mathop {\max} \sum _{{e_{ij}} \in E} {\log {p^{(1)}}({v_i},{v_j})}$

##### Second-order Proximity
有 first-order proximity，當然也有 second-order proximity
- 任兩節點的 second-order proximity，可以藉由當 $v_{i}$ 在 start node 的情況下，$v_{j}$ 為 end node 的機率來計算（conditional probability）
  - ${p^{(2)}}({v_j}|{v_i}) = \frac{\exp (y_j^T{y_i})}{{\sum _{k = 1}^{|V|} {\exp (y_k^T{y_i})}}}$
- 完整的 objective function 為：
  - $\mathcal{O}_{max}^{(2)} = \mathop {\max} \sum _{{\lbrace v_i, v_j\rbrace} \in \mathcal{P}} {\log {p^{(2)}}({v_j}|{v_i})}$
  - 其中 $\mathcal{P}$ 所代表的是在 graph 隨機抽樣出來的路徑集合，並不是所有的路徑都會被考慮進去

#### Minimizing Distance-Based Loss

node proximity 有兩種方法可以計算出，一種是使用 first-order proximity，另一藉由觀察邊計算出 empirical probability。
- node embedding 的方式可以使用 first-order proximity 的公式來計算
  - ${p^{(1)}}({v_i},{v_j}) = \frac{1}{{1 + \exp (- {y_i}^T{y_j})}}$
- empirical probability 可以藉由觀察邊來計算
   - $A_{ij}/\sum \nolimits _{{e_{ij}} \in E} {A_{ij}}$
   - $A_{ij}$ 是 edge 的權重




### Graph Kernel

### Generative Model
- Embed Graph Into The Latent Semantic Space
- Incorporate Latent Semantics for Graph Embedding

### Hybrid Techniques and Others