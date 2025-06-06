# Day-28 Network Visualization and Analysis Tools

## Network Visualization
視覺化是一個讓人又愛又恨的一樣工作，要把資料呈現出來又要好看真的很困難（也很痛苦）。像是 Albert-László Barabási 教授的[實驗室](https://barabasilab.com)就有分成兩部分，一部份做研究，另一部份是做藝術。有些是畫，也有立體的作品等等...。這些作品都可以在教授的 [instagram](https://www.instagram.com/p/CpVS_f9tlJE/) 上看到。

### 其他範例或是教學文章
- 其它視覺化範例可以參考 [NETWORK DIAGRAM](https://www.data-to-viz.com/graph/network.html)
- [How to Visualize a Social Network in Python with a Graph Database: Flask + Docker + D3.js](https://memgraph.com/blog/how-to-visualize-a-social-network-in-python-with-a-graph-database)

## Network Analysis Tools
雖然現在有許多 GNN 的 model 可以用來直接 train，但是比起「硬 train 一發」，我還是比較傾向要先了解數據本身，再根據數據本身的特性來決定要用什麼樣的 model，使用什麼樣的工具來處理（Sparsification 等等）。

本來以為 graph 之類的數據處理工具應該不多（畢竟現在大部分的資料都是 structure 的），但意外的找到滿多可以用的工具，以下是我找到的一些工具，有些是用來做 network analysis，有些是用來做 network visualization，有些則是兩者都可以。

另外還有找到一個叫做 [Gephi](https://gephi.org) 的開源工具，可以用來做 network analysis 和 visualization，感覺也是蠻有趣的，但是我沒有試過。

- [NetworKit](https://networkit.github.io/)
- [graph-tool](https://graph-tool.skewed.de/static/doc/index.html)
- [Plotly - Network Graphs in Python](https://plotly.com/python/network-graphs/)
- [scikit-network](https://scikit-network.readthedocs.io/en/latest/index.html)