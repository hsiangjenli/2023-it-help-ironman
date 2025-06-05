# Day-14-Paper Reading -- Graph Embedding - 續

## Problem Formalization
### Notation

- $g = (V, E)$ ---> graph
- $\hat{g} = (\hat{V}, \hat{E})$ ---> substructure of $g$
- $v_{i} \in V$ ---> node
- $e_{i,j} \in E$ ---> 連接 $v_{i}$ 跟 $v_{j}$ 的邊
- $A$ ---> $g$ 的關聯矩陣
- $A_{i}$ ---> 關聯矩陣的第 $i$ row
- $A_{i,j}$ ---> 關聯矩陣的第 $i$ row 第 $j$ column
- $f_v(v_i), f_e(e_{ij})$ ---> node 或 edge 的類別
- $\mathcal{T}^v, \mathcal{T}^e$ ---> node 或 edge 的類別的集合

### First-order proximity $S_{ij}^{(1)} = A_{i,j}$

是指計算 $v_{i} 與 v_{j}$ 之間邊的權重，也就是 $A_{i,j}$

![](../image/image-48.png)

- 像是上圖中的範例，$v_{1}$ 與 $v_{2}$ 之間邊的權重為 1.2，所以 $S_{1, 2}^{(1)} = 1.2$  
- $v_1$ 與其他節點的權重的表達方式：$S_{1}^{(1)} = [0, 1.2, 0.8, 0]$ 

### Second-order proximity $S_{i,j}^{(2)}$

簡單來說就是計算 $v_{i}$'s neighbors 跟 $v_{j}$'s neighbors 的相似度

所以 $S_{i,j}^{(2)}$ 的計算方式為：
- $S_{1}^{(1)} = [0, 1.2, 0.8, 0]$
- $S_{2}^{(1)} = [1.2, 0, 1, 0]$
- $S_{1,2}^{(2)} = cosin(S_{1}^{(1)}, S_{2}^{(1)}) = 0.36$

```python
import numpy as np

vec1 = np.array([0, 1.2, 0.8, 0])
vec2 = np.array([1.2, 0, 1, 0])

cos_sim = vec1.dot(vec2) / (np.linalg.norm(vec1) * np.linalg.norm(vec2))

print(cos_sim)

>>> 0.3551104121142175
```

### Higher-order proximity

如果是更高維度 $k$ 的 proximity，就是去計算 $v_{i}$ 跟 $v_{j}$ 在 $(k-1)$ order 的相似度，用公式表示：$cosine(S_{i}^{(k-1)}, S_{j}^{(k-1)})$

不過在更高維度的 proximity 上，使用的方法就不一定是計算 edge 的權重，也可以使用其他的 metric，例如：Katz index, rooted PageRank, Adamic-Adar index 等等。