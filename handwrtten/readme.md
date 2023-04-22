Handwritten
---

## 数据处理说明

**Requirements**
- python=3.8
- torch=1.12
- scikit-learn=1.1

**Running**
```bash
python preprocess.py  # 转换数据格式为本实验形式
```

**Usage**
```python
multi_view_x, labels = pickle.load(open('./train.pkl', 'rb'))
```
