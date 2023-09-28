# Day-13-Paper Reading -- Graph Embedding

> H. Cai, V. W. Zheng and K. C. -C. Chang, "A Comprehensive Survey of Graph Embedding: Problems, Techniques, and Applications," in IEEE Transactions on Knowledge and Data Engineering, vol. 30, no. 9, pp. 1616-1637, 1 Sept. 2018, doi: 10.1109/TKDE.2018.2807452.

這篇 paper 總共分成 5 個章節，分別是 Introduction、Problem Formalization、Problem Settings of Graph Embedding、Graph Embedding Techniques、Applications，因為內容太多應該會分成好幾天來看。

## Abstract
1. 定義 grpah embedding 以及相關的觀念
1. 點出目前 graph embedding 的問題以及未來的研究方向（效能、問題設定、技術、應用場景）

### Graph Embedding 的用處
1. Graph Analytics
1. Dimensionality Reduction
1. Representation Learning

graph embedding 是目前最有效率解決 graph analytics 問題的方法，因為它將 graph 轉換成低維度的向量的同時也保留了 graph 的結構資訊。

## Introduction
Graph embedding 講簡單一點可以說成 graph data 資料前處理的一種方法（包括但不限於），graph embedding 之後的資料可以應用在各種不同的應用場景，像是 node classification、node clustering、node retrieval/recommendation、link prediction 等等...

雖然有很多開源程式碼專注在 distributed graph data processing 的框架，希望這些框架可以用更有效率的方式來儲存以及加速運算，但是這些方法還是比不上 graph embedding 的效率。graph embedding 的範圍包括 node / edge / substructure / whole-graph。

一開始 graph embedding 是用來降低維度的，但從 2010 年開始有人將 graph embedding 完的結果輸入到模型中，並且結合上其他的資料。為了產生更好的 graph embedding 結果，像是有人開始使用 deep learning 的方法或是設計新的目標函示。

graph embedding 解決了 graph analytics 跟 representation learning 的問題
- representation learning --> 因為 graph embedding 就是將 graph 轉換成低維度的向量的同時保持 graph 的結構資訊
- graph analytics --> 因為將 graph 轉成低維度的向量，所以讓 graph analytics 的問題變得更容易

graph embedding 最困難的部分在於問題設定以及技術，像是 graph 的輸入又分成很多種，像是 homogenous、heterogenous、帶有其他資訊的 graph 等等...。

在文章中作者將 graph embedding 分成四種類型，分別是 node embedding、edge embedding、hybrid embedding、whole-graph embedding，而這四種各有各的 criteria 去衡量他們的優劣。

### Contribution
1. 基於 graph embedding 的問題設定的方式分別去統整他們所遇到的挑戰，在了解目前的現況後同時提供未來的研究方向
1. 不僅是將現有的方法進行分類列出，更總結出為什麼這些方法可以解決特定的問題
1. 提供了 4 個未來研究方向，包括：效能、問題設定、技術、應用場景

### 問題設定以及技術的整體架構
- Graph Embedding Problem Settings
  - Graph Embedding Input
  - Graph Embedding Output
- Graph Embedding Techniques
  - Matrix Factorization
  - Deep Learning
  - Edge Reconstruction
  - Graph Kernel
  - Generative Model
