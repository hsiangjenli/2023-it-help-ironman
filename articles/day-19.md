# Day-18-Paper Reading -- Graph Embedding - 續

## Graph Embedding Techniques
### Edge Reconstruction Based Optimization
#### Minimizing Margin-Based Ranking Loss

在 minimizing margin-based ranking loss 中，edge 代表的是一組 node 之間的關係

重點在於一個點的 embedding 跟其他相關的 node 的 embedding 應該要比其他不相關的 node 的 embedding 要更接近。

> **objective function（normal）**
> 
> $\mathcal{O}_{rank} = \min \sum \limits _{v_i^+ \in V_i^+} \sum \limits _{v_i^- \in V_i^-} \max \lbrace 0,\gamma -
 s(v_i, v_i^+)+s(v_i, v_i^-)\rbrace$
> - $v_i^+$ 代表的是跟 $v_i$ 有關係的 node
> - $v_i^-$ 代表的是跟 $v_i$ 沒有關係的 node
> - $\gamma$ 是 margin 的大小
> 
> 目標是：  
> 1. min loss rank
> 1. max $s(v_i, v_i^+)$ 跟 $s(v_i, v_i^+-)$ 之間的 margin

> **objective function（knowledge graph embedding）**
> 
> $\mathcal{O}_{rank}^{kg} = \min \mathop{\sum}_{{<h,r,t> \in \mathcal{S}, \atop <h^{\prime},r,t^{\prime}>
 \notin \mathcal{S}}} \max \lbrace 0,\gamma + f_r(h,t)-f_r(h^{\prime},t^{\prime})\rbrace$
> knowledge graph 是由三元組所組成，分別是 <head, realation, tail>，所以 objective function 要稍微修改
> - $f_r(h,t)$ 代表的是針對關係 r，在 embedding 中 head 跟 tail 的距離分數。

### Graph Kernel
