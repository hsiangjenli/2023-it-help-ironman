# Day-27 pyG + Node2Vec + Memgraph

## 與 Memgraph 連線

```python
conn = mgclient.connect(host="localhost", port=7687)
cursor = conn.cursor()
```

### 匯出 node 的 properties（x） 跟 label（y） 
```python

```