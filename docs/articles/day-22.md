# Day-22-pyG 匯入資料集

## `torch_geometric.data`

如果可以，直接使用 pyG 的程式碼匯入資料集，可以省去很多麻煩。自己用 pytorch 匯入資料集的話，像是這個 graph 有多少個 node，幾條 edge 等等的資訊都要自己處理。

### pyG 的名詞解釋
在匯入資料集之前，會看到很多 PARAMETER，這些 parameter 是用來描述資料集的，所以就來看看在 pyG 中，是用什麼名詞來描述 node 和 edge
- `x`：node 的 feature matrix，shape 為 `(num_nodes, num_node_features)` 
- `edge_index`：edge 的 index，shape 為 `(2, num_edges)`，是 COO format，可以參考[邻接矩阵的COO格式](https://blog.csdn.net/raelum/article/details/125991229)這篇文章，簡單來說就是 adjacency matrix 的改良版
- `edge_attr`：edge 的 feature matrix，shape 為 `(num_edges, num_edge_features)`
- `y`：target vector，shape 為 `(num_nodes, )`，通常是 node 的 label


### `torch_geometric.data.Data`
用於 homogeneous graph 的資料結構，在建立好 `Data` Object 之後使用 `from_dict` method 匯入 dictionary。

### `torch_geometric.datasets`
pyG 提供了很多資料集，可以直接使用，這裡使用 `Cora` 這個資料集來做範例。

根據這篇[文章](https://aistudio.baidu.com/projectdetail/2246479?shared=1)的內容，我們可以稍微了解一下這個資料集。`train_mask` `val_mask` `test_mask` 這三個參數是用來區分哪些是用來訓練、驗證、測試的。

- `node` 為 2708 篇 paper
- `node feature` 是單詞，總共有 1433 個單詞
- `edge` 為 10556 條引用關係
```python
from torch_geometric.datasets import Planetoid

dataset = Planetoid(root='data/Cora', name='Cora')
data = dataset[0]
data

>>> Data(x=[2708, 1433], edge_index=[2, 10556], y=[2708], train_mask=[2708], val_mask=[2708], test_mask=[2708])
```

## Reference
- [基于Pytorch的PyTorch Geometric（PYG）库构造个人数据集](https://blog.csdn.net/rothschild666/article/details/123799943)