# Day-10-Network Science 的任務

## Link Prediction（連結預測）
Link Prediction 是用來預測任兩個節點之間未來是否會有連結的一種方法。透過分析訓練集裡面節點的連結關係，可以得到一些特徵，例如計算節點的 degree、Jaccard coefficient、Adamic/Adar、Common Neighbors 等等，再透過這些特徵來訓練一個機器學習的模型，這樣就可以用來預測未來是否會有連結。
## Node Classification（節點分類）
Node Classification 跟一般的分類模型概念差不多。只是在 Network Science 裡面，會比傳統的結構型資料多了節點之間的連結關係。透過這些連結關係，可以提供更多的資訊給模型，讓模型可以更好的進行分類。
## Community Detection（社群偵測）
Community Detection 是藉由分析節點之間的連結關係，將節點分群（關係緊密的節點）的一種方法。屬於非監督式學習的一種，因此資料不需要事先標記好，衡量分群的好壞可以透過 modularity 來進行衡量。簡單來說，就是希望同一個社群裡面的節點之間的連結關係要比社群之間的連結關係要緊密（最佳化的公式）。