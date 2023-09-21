# Day-08-Network Model--Watts–Strogatz model

## 作者
Watts-Strogatx model 是用來產生具有 small-world 性質的 rqandom graph 數學模型，由 Duncan J. Watts 跟 Steven Strogatz 在 1998 年發表。這個模型是基於上一篇所提到的 ER model 為基礎進行改進。在 ER model 中，因為每個節點之間連接的機率都是一樣的，所以在 ER Model 裡面不容易產生 local clustering 和 triadic closures 的結構，導致其 clustering coefficient 很低；另外在現實生活中，有很多 hub（樞紐），但是 ER Model 並沒有將其考慮進去，所以 ER Model 是 Poisson Distribution，而非現實生活常出現的 Power Law Distribution。

## 模型定義

- 
- 起始節點到距離 d 的預期節點數量是：$N(d) \approx 1 + \left\langle k \right\rangle + \left\langle k \right\rangle ^2 + ... + \left \langle k \right\rangle ^d = \frac{\left\langle k \right\rangle ^{d+1}-1}{\left\langle k \right\rangle-1}$
