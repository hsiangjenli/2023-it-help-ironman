# Day-21-Paper Reading -- Graph Representation Learning

> Graph representation learning in bioinformatics: trends, methods and applications


這篇 paper 總共分成 5 個章節，分別是 Introduction、Graph Representation Learning: a brief overview、Applications in Bioinformatics、Challenges and Opportunities、Conclusion。

本篇 paper 主要的貢獻有三個：
1. 分析了 graph embedding 和 graph neural network 的方法。並且將 graph embedding 的方法細分成 homogeneous graph embedding、heterogeneous graph embedding 和 attribute graph embedding。
1. 總結了 graph representation learning 在 bioinformatics 的應用，從  molecular level 到 genomics、pharmaceutical 跟 healthcare systems 等等。
1. 同時也整理了一些 open source 的 graph representation learning 的資源。

## Introduction
> ![](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/bib/23/1/10.1093_bib_bbab340/1/m_bbab340f1.jpeg?Expires=1699425920&Signature=SLMv37E8~~3kcG-I33AtMTWtLN9hNM1s9VTq5yWS9tzYxP8bxq9vs4P2OWsUm4T4m1evU~Pg4de855qvT3eWu4lg3d0dH36xSMLq1AvtDjzRPoDQAf2pTKIzgLD2D~Yr7zu6YeHElE7Do9Dvj6xFI4yiZqncKFkG27xgY~S~KmYo0kk8oJPUvF51kvvrxuUVSUeCX9vcuJSf514MM1-nvqOwZrSlE-apinyJodM4k-OVtUl~3dBEDEl0SfhOsekv6KeC6EI8wFNxtkN78YrqGLmW091qYTSo1WPJObHuoqoWg5Mh9WSEkRbpx~P9nClcDw--wa4rUkmgVjZ80onGAg__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)
> 圖片來源：Graph representation learning in bioinformatics: trends, methods and applications（https://doi.org/10.1093/bib/bbab340）
>
> 這張圖的 (A) (B) 是在講 graph structure 跟一般 grid like structure 的差別，以及 graph embedding 的意思就是將 graph structure 嵌入到 embedding space。  
> 
> (C) 跟 (D) 是在講 graph neural network 跟 graph generative model 的差別。  
> 
> (C) graph neural network 是藉由多種的 message aggregation 以及 propagation 的方式來找到最佳的 embedding。  
> 
> (D) graph generative model 是藉由輸入的 distribution 來生成 graph。