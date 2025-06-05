# Day-09-Network Model--Scale-free network
## Scale-free network 的特性
Scale-free network 是一種具有 power law distribution 的網路圖。在 scale-free network 中，有一些節點的 degree 會比其他節點來的高，這些節點被稱為 hub（樞紐）。

### Preferential attachment
Scale-free network 可以藉由 preferential attachment 來產生。Preferential attachment 是一種機制，當一個新的節點加入網路圖的時候，會優先選擇 degree 較高的節點來連接（這樣就可以產生一個有 Hub 的網路圖）。

## 公式推導

在 Network Science 這本書裡面，作者舉的一個例子。如果 WWW 是一個 random network，那它的 degree distribution 應該是 Poisson distribution，但事實並非如此。作者將圖改成 log-log scale plot 之後發現將資料點連起後會很接近一條直線，這就代表 WWW 是一個 power-law distribution。

### Log-log scale - 線性迴歸
- $\ln{p(k)} = C - \gamma \ln(k)$
- 對兩邊取指數，可以得到 $p_{k} = k^{-\gamma}$
- 其中 $\gamma$ 稱作 power law exponent，會在前加上負號是因為斜率是負的
- $C$ 稱作 normalization constant

如果想要知道 k 剛剛好等於某個 degree 的機率為多少的時候，我們可以用下面的兩種公式進行計算（分別為假設 degree 為 discrete 或是 continuous）：

### Discrete 
1. 把所有可能的 degree 加總之後，機率要剛好等於 1 ，$\sum\limits_{k = 1}^\infty  {p_k }  = 1$
1. 也可以寫成 $C \sum\limits_{k=1}^\infty k^{-\gamma} = 1$
1. $C = \frac{1}{\sum\limits_{k=1}^\infty k^{-\gamma}}$
1. 這個式子剛好可以用 Riemann zeta 函數來表示，$C = \frac{1}{\zeta (\gamma)}$
1. 所以 $p_k = \frac{k^{-\gamma}}{\zeta (\gamma)}$

### Continuous
1. 使用積分處理，$\int\limits_{k_{\min } }^\infty  {p(k)dk}  = 1$
1. 也可以寫成 $C \int\limits_{k_{\min } }^\infty k^{-\gamma} dk = 1$
1. 進行交換律之後可以得到 $C = \frac{1}{{\int\limits_{k_{\min } }^\infty  {k^{ - \gamma } dk} }}$
1. 對 $k$ 進行積分，可以得到 $C = \frac{1}{{\frac{1}{{1-\gamma}} {k^{1 - \gamma } } |_{k_{\min } }^\infty  }}$
1. 因為 $\infty$ 會變成 0，所以就只計算 $k_{min}$，可以化簡成 $C = (1-\gamma)k_{min}^{\gamma-1}$
1. $p(k) = (1-\gamma)k_{min}^{\gamma-1}k^{-\gamma}$

## 參考資料
- [On the Power Law Statistical Distribution of Observations](https://indico.ictp.it/event/a08182/session/44/contribution/28/material/0/0.pdf)
- [Network Science](http://networksciencebook.com/chapter/4#introduction4)

