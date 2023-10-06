# Day-21-Paper Reading -- Graph Representation Learning

> Graph representation learning in bioinformatics: trends, methods and applications


這篇 paper 總共分成 5 個章節，分別是 Introduction、Graph Representation Learning: a brief overview、Applications in Bioinformatics、Challenges and Opportunities、Conclusion。

本篇 paper 主要的貢獻有三個：
1. 分析了 graph embedding 和 graph neural network 的方法。並且將 graph embedding 的方法細分成 homogeneous graph embedding、heterogeneous graph embedding 和 attribute graph embedding。
1. 總結了 graph representation learning 在 bioinformatics 的應用，從  molecular level 到 genomics、pharmaceutical 跟 healthcare systems 等等。
1. 同時也整理了一些 open source 的 graph representation learning 的資源。

## Introduction
> ![](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bib/23/1/10.1093_bib_bbab340/1/m_bbab340f1.jpeg?Expires=1699425920&Signature=SLMv37E8~~3kcG-I33AtMTWtLN9hNM1s9VTq5yWS9tzYxP8bxq9vs4P2OWsUm4T4m1evU~Pg4de855qvT3eWu4lg3d0dH36xSMLq1AvtDjzRPoDQAf2pTKIzgLD2D~Yr7zu6YeHElE7Do9Dvj6xFI4yiZqncKFkG27xgY~S~KmYo0kk8oJPUvF51kvvrxuUVSUeCX9vcuJSf514MM1-nvqOwZrSlE-apinyJodM4k-OVtUl~3dBEDEl0SfhOsekv6KeC6EI8wFNxtkN78YrqGLmW091qYTSo1WPJObHuoqoWg5Mh9WSEkRbpx~P9nClcDw--wa4rUkmgVjZ80onGAg__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)
> > 圖片來源：Graph representation learning in bioinformatics: trends, methods and applications（https://doi.org/10.1093/bib/bbab340）
>
> 這張圖的 (A) (B) 是在講 graph structure 跟一般 grid like structure 的差別，以及 graph embedding 的意思就是將 graph structure 嵌入到 embedding space。  
> 
> (C) 跟 (D) 是在講 graph neural network 跟 graph generative model 的差別。  
> 
> (C) graph neural network 是藉由多種的 message aggregation 以及 propagation 的方式來找到最佳的 embedding。  
> 
> (D) graph generative model 是藉由輸入的 distribution 來生成 graph。

> ![](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bib/23/1/10.1093_bib_bbab340/1/m_bbab340f2.jpeg?Expires=1699425920&Signature=YQfBTN6F~kfdXP4eSqxgT2ZOvNfTM0tFdxoBBLXt75RDjmgDi7UNRV9y5jAg7mQ3Fl7FB2-zp8z4a2nin7Qg8siNYvoXKR7HtLUGz5Ir3nUp5ndgy5oWWHXaXYqPySPkDpXrM3Cnj1xsZwB3aCabDgdFLuimOV1dXSsQ7KCXgJ7Dbl1qETyKPienQqkORW~YH0lbOiwSY9NOVy-wm-oBvS07vqw6ysZXQgdpraoy5JlWn1h1Bpfz~sg6nQuvo-Tf7H320Y4hsB2BabQQ4aPgA~9AAb4Zx3VqmG01HLPlcgrjeKoCKTljyykRdw8PAsRlFHjNCU-KDV164Q~tv95WoA__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)
> > 圖片來源：Graph representation learning in bioinformatics: trends, methods and applications（https://doi.org/10.1093/bib/bbab340）
> 
> 這張圖是在講 graph embedding 跟 graph neural network 的差別。
>
> 從內文感覺上來說，graph embedding 比較像是資料前處理，處理完後的資料可以套用到其他的機器學習模型上。但是 graph neural netwrok 是一個 end-to-end 的模型，可以直接輸入 graph 並且輸出預測的結果。

## Graph Representation Learning: a brief overview

> ![](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bib/23/1/10.1093_bib_bbab340/1/m_bbab340f3.jpeg?Expires=1699425920&Signature=ck8wadfNgxhfelncL7t~vaLbeuDmcW0ROIj1yNOPFpYBzYQxm7qxVm3pMgl7fWp9i6UvdKBLDVliWlAr6VHJrjJ~WNdrZBzrC15EMWLkwoOqCMxlj7nFoQ0zjsXPX-f6X8bJ1bhR676WsOxACubdvlvb3RiVPu0mr~c0cVaUw0i5XXZijGkVEXe~LNAcsAY0UQjIHvfQEk8wnz8S0AMLk9dJCGtnsrFaTgfY~VBkny0-syL-D-n7yiUzaiTMZ6fWlyeCM3MxdBlYaqsPDqHpT3kn776vOb0yCZiF8FXRAG88nIAUwEkirx4JmBzoY3ybO7kbYpIqDfuE2ovfUujisA__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)
> > 圖片來源：Graph representation learning in bioinformatics: trends, methods and applications（https://doi.org/10.1093/bib/bbab340）
> 
> 這篇 paper 跟上一篇 paper 最主要的差別就是這篇 paper 比較沒有特別把 objective function 寫出來，但是因為這篇是比較新的 paper，所以提到了許多新的 graph embedding 的方法。

其中，我對 heterogeneous graph 跟 attribute graph 的定義有點好奇差別在哪裡，所以著重在解釋這兩種 graph 的差別。其他介紹不同 embedding 的方法的部分就先跳過。

### Heterogeneous graph embedding
>  node 跟 edge 都會有不同的屬性。

heterogeneous graph embedding 的方法大致可以分成三種：
1. meta-path-based  
   從內文看起來 meta-path-based 的方法應該是 random walk 的變體，主要的差別在於 meta-path 會限制住 random walk 的方向，減少在 heterogeneous graph 上的 traversal 的複雜度。
1. decomposition-based  
   把 heterogeneous graph 分解成比較小的 homogeneous 或是 bipartite graph。
1. deep learning-based methods


### Attribute graph embedding
> node 會有不同的屬性，但是 edge 的屬性都是一樣的。

## Open source resources
### 開源框架
- [OpenNE](https://github.com/thunlp/OpenNE/tree/pytorch)
- [CogDL](https://github.com/THUDM/cogdl)
- [PyTorch Geometric (PyG)](https://github.com/rusty1s/pytorch_geometric)
- [Deep Graph Library (DGL)](https://github.com/dmlc/dgl)
- [Dive into Graphs (DIG)](https://github.com/divelab/DIG)
- [Graphvite](https://github.com/deepgraphlearning/graphvite)
- [Graph-Learn](https://github.com/alibaba/graph-learn)
- [Paddle Graph Learning (PGL)](https://github.com/PaddlePaddle/PGL)

### open-source implementations of graph representation learning algorithms
> 這邊挑幾個有趣的，改天來看看到底這些方法是怎麼實作的。
1. [homogenous - GraRep](https://github.com/ShelsonCao/GraRep)
1. [homogenous - HOPE](http://git.thumedia.org/embedding/HOPE)
1. [homogenous - Deepwalk](https://github.com/phanein/deepwalk)
1. [Heterogeneous - metapath2vec](https://ericdongyx.github.io/metapath2vec/m2v.html)
1. [Heterogeneous - GATNE](https://github.com/THUDM/GATNE)

