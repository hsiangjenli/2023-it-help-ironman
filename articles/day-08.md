# Day-08-Network Model--Watts–Strogatz model

## 作者介紹
Watts-Strogatx model 是用來產生具有 small-world 性質的 rqandom graph 數學模型，由 Duncan J. Watts 跟 Steven Strogatz 在 1998 年發表。這個模型是基於上一篇所提到的 ER model 為基礎進行改進。在 ER model 中，因為每個節點之間連接的機率都是一樣的，所以在 ER Model 裡面不容易產生 local clustering 和 triadic closures 的結構，導致其 clustering coefficient 很低；另外在現實生活中，有很多 hub（樞紐），但是 ER Model 並沒有將其考慮進去，所以 ER Model 是 Poisson Distribution，而非現實生活常出現的 Power Law Distribution。

## Small World 的特性
small world model 有一個很著名的實驗，叫做 six-degree of separation（六度分隔）。這個實驗是由 Stanley Milgram 在 1967 年所提出的。實驗內容為 Stanley Milgram 寄出 60 封信給參加者，並且要求參加者將信轉交給他們認識的人，但是只能透過朋友轉交。最後，Stanley Milgram 發現平均只需要 6 個人就可以將信轉交給目標（實際成功寄回到目的的只有 5%）。

因此，這個實驗想傳達的資訊是人與人的聯繫比你所預想的還要更加的緊密。
## 數學公式推導

1. 假設平均 degree（平均有幾個 neighbor）：$\left\langle k \right\rangle$
1. Distance = 1 的時候，我們會有 $\left\langle k \right\rangle$ 個節點
1. Distance = 2 的時候，我們會有 $\left\langle k \right\rangle^2$ 個節點，依此類推後
1. 起始節點到距離 d 的預期節點數量是 $N(d) \approx 1 + \left\langle k \right\rangle + \left\langle k \right\rangle ^2 + ... + \left \langle k \right\rangle ^d$
   - 也就是把所有距離在 0 到 d 的節點數量加起來，可用等比級數和公式 $\frac{a(1-r^n)}{1-r}$（有些人會分子分母都乘以 -1）
   - $a = 1$, $r = \left\langle k \right\rangle$, $n = d + 1$
   - 最後的公式如右所示 $\frac{\left\langle k \right\rangle ^{d+1}-1}{\left\langle k \right\rangle-1}$
1. $N(d_{max}) \approx N$，也就是說當距離到達最大的時候，我們的節點數量會大約等於總節點數量
1. 這邊假設 $\left\langle k \right\rangle$ 是一個遠大於 1 的數字，我們就可以把 -1 省略掉
1. 所以當 Distance = $d_{max}$ 的時候，我們就會有 $\left\langle k \right\rangle ^{d_{max}}$ 個節點，也就是 $N$
1. $\left\langle k \right\rangle ^{d_{max}} = N$，使用換底公式後，我們可以得到 $d_{max} = \frac{ln(N)}{ln(\left\langle k \right\rangle)}$