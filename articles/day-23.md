# Day-23-pyG 的 `nn.Module` 中的 aggregation 意思

在 `torch_geometric.nn` 中有很多 Module 可以使用，希望可以稍微了解一下這些 Module 的使用情境。

![](../image/image-50.png)

## Aggregation Operators

今天先 focus 在 `aggregation operators` 這個部分，根據官網的說明，aggregation operators 在 message passing 中扮演很重要的角色。

在 [github issue](https://github.com/pyg-team/pytorch_geometric/issues/4712) 中作者有解釋到為何會有這個 aggregation operators。主要是因為 aggregation 這個概念在 message passing 跟 global readouts 中都有用到，但是在使用上是分開的，所以作者希望可以把這兩個部分統一起來，更方便重複使用。

裡面有介紹幾種不同的 aggregation operators 它們的特色。像是比較基本的 mean aggregation 可以抓到 neighborhood 的 distribution；max aggregation 可以找到最具代表性的 element；sum aggregation 可以學到 structural graph properties，像是 degree 之類的資訊。

其中比較有趣的是裡面有提供 learnable aggregation operators，以 `SoftmaxAggregation` 為例，它的原始 [paper](https://browse.arxiv.org/pdf/2006.07739.pdf) 裡面說到，這個 aggregation operator 是希望可以 generalize mean-max aggregation。

在 pyG 的公式如下所示
- $\mathrm{softmax}(\mathcal{X}|t) = \sum_{\mathbf{x}_i\in\mathcal{X}}
\frac{\exp(t\cdot\mathbf{x}_i)}{\sum_{\mathbf{x}_j\in\mathcal{X}}
\exp(t\cdot\mathbf{x}_j)}\cdot\mathbf{x}_{i}$
- $t$ 的意思是一種連續 variable，稱作 inverse temperature
- 在公式中，當 $t$ 接近 0 時，就會變成 mean aggregation；當 $t$ 接近無限大時，就會變成 max aggregation

> ![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*2tCd7QgYOwexWCIqMhV70A.png)
> 圖片來源：[A Principled Approach to Aggregations](https://medium.com/@pytorch_geometric/a-principled-approach-to-aggregations-983c086b10b3)

> ![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*TRThuWpGywioT0BV6_y45Q.png)
> 圖片來源：[A Principled Approach to Aggregations](https://medium.com/@pytorch_geometric/a-principled-approach-to-aggregations-983c086b10b3)
> 
> 這張圖片是用來解釋在不同 graph 結構（異構圖）底下使用不同 aggregation 後能不能區分出兩個 graph 是不同的。  
> 
> **橘色**代表使用 aggregation operator 後會無法區分兩個 graph 的差別。

## Reference

- [PyTorch 中的 ModuleList 和 Sequential: 区别和使用场景](https://blog.csdn.net/byron123456sfsfsfa/article/details/89930990)

- [A Principled Approach to Aggregations](https://medium.com/@pytorch_geometric/a-principled-approach-to-aggregations-983c086b10b3)
- [[Roadmap] torch_geometric.nn.aggr](https://github.com/pyg-team/pytorch_geometric/issues/4712)