# Day-19-Paper Reading -- Graph Embedding - 續

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
意思是整個 graph 可以被分解成包含所有的 substructure 的向量。

graph kernel 有兩種功能（？）：
1. grpah kernel 是 R-convolution kernel 的實例，但是是屬於一種更通用的方式，使用遞迴的方式來分解結構化的物件。
1. 可以將 graph kernel 當作 graph 的向量，並且使用 inner product 來計算兩個 graph 之間的相似度。

graph kernel 有三種類型：
1. graphlet
1. subtree patterns
1. random walk

#### graphlet
graphlet 是一個大小為 k 非同構的子圖。假設有一個 $G$，可以被分解成不同的 graphlet，使用 { $g_{1}, g_{2} ... g_{d}$ } 表示。然後使用特殊的方式將這些 graphlet 轉換成 d 維的向量，這個向量稱為 $y_{G}$，這個向量中的每一個元素代表的是 $G$ 中包含 $g_{i}$ 的個數。

#### subtree patterns
在這個 kernel 裡面，graph 會被分解成它的 subtree patterns。

#### random walk
在這個 kernel 裡面，graph 會被分解成隨機路徑。並且會記錄下這種路徑的出現次數，這些特徵可以用來當作這個 graph 的特徵。