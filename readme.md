多视角深度学习研究团队数据集处理规范
---

## 重要说明

数据集必须在`readme.md`中注明数据集名称、出处、下载地址等信息，并提供运行命令。
部分数据集链接
链接：https://pan.baidu.com/s/1tH_yt8fg6cyBqsl4J5dS8A 
提取码：1234 
--来自百度网盘超级会员V7的分享

## 预处理规范

### 1. 下载数据集

必须提供数据集下载链接或数据集源文件。压缩包要提供解压方法。例如MultiLingualReuters:
```bash
curl -O https://archive.ics.uci.edu/ml/machine-learning-databases/00259/rcv1rcv2aminigoutte.tar.bz2
tar jxvf rcv1rcv2aminigoutte.tar.bz2  # 解压
```

### 2. 数据预处理

必须提供可直接执行的程序及其运行运行环境，例如：

**Requirements**
- python=3.8
- torch=1.12
- scikit-learn=1.1

**Running**
```bash
python preprocess.py
```

运行之后获得3个文件：`train.pkl`,`valid.pkl`,`test.pkl`可供实验使用（有些实验不需要`valid.pkl`）。

以`train.pkl`示例数据格式：
```python
[
    #多视角特征。dict key 表示视角编号；array(...)代表该视角的样本
    {0:[array(...), array(...), ...], 1:[array(...), array(...), ...], ...},
    [int, int, ...]  # 每个样本的标签
]
```
其中，多视角特征的数据类型为`numpy.float32`，标签的数据类型为`numpy.int64`。这样规定是为了适应大多数框架及运行环境，减少不必要的麻烦。

**Usage**

实验时，使用以下语句读取多视角数据：
```python
multi_view_x, labels = pickle.load(open('./train.pkl', 'rb'))
```

基于`torch`框架，实验模版参考[xdmvteam/TMC](https://github.com/xdmvteam/TMC)。

## Git上传规范

为减小仓库体积，凡是总体积超过10MB的数据集，不允许直接上传到仓库，必须提供下载方式。
