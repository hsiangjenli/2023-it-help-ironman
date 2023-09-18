# Day-05

## Graph 的資料結構

![](../image/image-25.png)
## Adjacency Matrix

![](../image/image-30.png)

最基本儲存圖的資料結構叫做 Adjacency Matrix 是一個 $|V|\times |V|$ 的二維陣列，假如節點跟節點之間有邊連接就填入 1（或是權重的值）；其餘就填入 0。它的優點在於簡單、好懂、新增或是刪除邊很方便。缺點就是占據非常大的空間 $O(V^{2})$，尤其是整個圖中的邊不多，二維陣列裡面就會有很多 0。計算 Adjacency Matrix 所需的時間為 $O(V)$

> 所需空間：$O(V^{2})$  
> 時間複雜度（Query）：$O(1)$  
> 適用場景：稠密圖

## Sparse Matrix
![](./../image/image-32.png)

有鑑於 Adjacency Matrix 不適合太過稀疏的圖，因此引申出一種新的資料結構稱為 Sparse Matrix，這種資料結構只會保存有邊的資料。

> 所需空間：$O(E)$  
> 時間複雜度（Query）：$O(\log E)$（可用二分法）  
> 適用場景：稀疏圖

## Adjacency List
![](../image/image-31.png)

Adjacency List 是一種以每個節點作為鍵（key），並與其相連的節點列表作為值（value）的資料結構。每個節點的鍵（key）對應到一個 list，其中包含與該節點相連的其他節點。


> 所需空間：$O(V+E)$  
> 時間複雜度（Query）：$O(V)$  
> 適用場景： 稀疏圖
## Incidence matrix


<!-- |Adjacency Matrix|Adjacency List|Incidence matrix|
|:--------------:|:------------:|:--------------:|
|![](./../image/image-26.png)|![](./../image/image-27.png)|| -->

## 參考資料
- [Graph Data Structure And Algorithms](https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/)
- [Adjacency matrix meaning and definition in DSA](https://www.geeksforgeeks.org/adjacency-matrix-meaning-and-definition-in-dsa/)
- [Graph Representation: Edge list, Adjacency Matrix, and Adjacency lists](https://www.jomaclass.com/blog/graph-representation-edge-list-adjacency-matrix-and-adjacency-lists)
- [Data Structures Tutorials - Sparse Matrix with an example](http://btechsmartclass.com/data_structures/sparse-matrix.html)
- [Comparison between Adjacency List and Adjacency Matrix representation of Graph](https://www.geeksforgeeks.org/comparison-between-adjacency-list-and-adjacency-matrix-representation-of-graph/)