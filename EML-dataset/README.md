
##用于EML的CHB-MIT数据集的预处理过程

###1. 下载数据集
https://physionet.org/content/chbmit/1.0.0/
放在\dataset\eeg\data\raw_data文件夹下

###2. 数据预处理

**Requirements**
+ python 3.8
+ numpy 1.23
+ pytorch 1.12
+ scikit-learn 1.2
+ mne 0.23.4
+ scipy 1.1.0


**Running**
```bash
python record.py
```

运行后将得到数据集的癫痫发作时间片文档
注：这样提取的癫痫发作时间片中包含部分片段采集通道不同于其他片段，可以根据自己的需求选择
推荐直接使用已经选取后提取好的文档record.txt

```bash
python channel.py
```
注：选择record.txt中所需的病人发作片段，在channel.py的segments下设置
如果使用所提供的预设的record.txt，则选取的通道为'FP1-F7', 'F7-T7', 'T7-P7', 'P7-O1', 'FP1-F3', 'F3-C3', 'C3-P3', 'P3-O1', 'FP2-F4', 'F4-C4', 'C4-P4', 'P4-O2', 'FP2-F8', 'F8-T8', 'T8-P8-0', 'P8-O2', 'FZ-CZ', 'CZ-PZ', 'P7-T7', 'T7-FT9', 'FT9-FT10', 'FT10-T8', 'T8-P8-1'
第六号病人为：'FP1-F7', 'F7-T7', 'T7-P7', 'P7-O1', 'FP1-F3', 'F3-C3', 'C3-P3', 'P3-O1', 'FP2-F4', 'F4-C4', 'C4-P4', 'P4-O2', 'FP2-F8', 'F8-T8', 'T8-P8-0', 'P8-O2', 'FZ-CZ', 'CZ-PZ', 'T8-P8-1', 'FC1-Ref', 'FC2-Ref', 'FC5-Ref', 'FC6-Ref'
请根据自己实际病人、通道和发作片段的选取情况按需设置

```bash
cd dataset/eeg/preprocessing/ && matlab  -nodesktop -nosplash -r preprocessing_data.m
```
提取特征过程，运行后获得对应的matlab文件

```bash
python preprocess.py
```
运行之后获得train.pkl和valid.pkl