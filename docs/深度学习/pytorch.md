# pytorch

## python基础

### pickle

+ **pickle**：对象序列化（Serialization）和反序列化（Deserialization）的内置工具

### dict

只想拿名字？用 disease_counts.keys()
只想拿数值？用 disease_counts.values()
全都要？用 disease_counts.items()

## 学习工具

+ dir() &emsp;#打开，看见

+ help() &emsp;  #说明书

## numpy

Numpy 是 Python 处理数值数组的核心库，PyTorch 张量的操作几乎和 Numpy 一致，先学最核心的数组操作。

### 导入numpy库

```python
import numpy as np
```

### 创建numpy数组

```python
arr1 = np.array([[1, 2], [3, 4]])  # 2行2列的二维数组
arr2 = np.ones((2, 2))             # 全1数组（和torch.ones一致）
```

+ np.array()接收Python
列表作为参数，生成NumPy数组

### 数组形状

```python
 作为数组方法
arr_2x3 = arr.reshape(2, 3)      # shape: (2, 3)
arr_flat = arr.reshape(-1)       # 展平为一维
加上copy则为复制
```

### 数组运算

```python
print(arr1 + arr2)  # 逐元素相加：[[2,3],[4,5]]
print(arr1 @ arr2)  # 矩阵乘法（和torch.matmul一致）
```

### 广播功能

标量和NumPy数组之间进行运算，则标量会和NumPy数组的各个元素进行运算

```python
>>> t = np.array([1.0, 2.0, 3.0])
>>> 1.0 + t
array([ 2., 3., 4.])
>>> 1.0 / t
array([ 1. , 0.5 , 0.33333333])
```

## matplotlib

### 绘制简单图形

```python
import numpy as np
import matplotlib.pyplot as plt
# 生成数据
x = np.arange(0, 6, 0.1) # 以0.1为单位，生成0到6的数据
 y = np.sin(x)
# 绘制图形
1.6 Matplotlib  17
plt.plot(x, y)
plt.show()
```

## tensor操作

### 张量：张量，多维数组

+ 0 维张量：单个数字（如 5）→ 标量
+ 1 维张量：[1,2,3] → 向量（比如一个人的身高、体重、年龄）
+ 2 维张量：\[[1,2],[3,4]] → 矩阵（比如 100 个样本，每个样本 2 个特征）

+ **创建tensor**：

```python

import torch

创建一个未初始化的 nxn 的 张量
x = torch.empty(n, n)
print(x)

创建一个随机初始化的张量
x = torch.rand(n, n)
print(x)

创建一个全 0 的张量，并指定数据类型为 long
x = torch.zeros(n, n, dtype=torch.long)
print(x)
```

## 加载数据

### dataset

**dataset**：提供一种方式获取数据及其label

+ 如何获取每一个数据及其label
+ 告诉我们一共有多少数据

### dataloader

**dataloader**：为后面的网络提供不同的数据形式

## 函数

+ **os.listdir()** 列出指定目录下所有文件和子目录名称，返回列表类型
+ **os.path.join()** 连接目录与文件名或目录，返回字符串类型

## TensorBoard

+ **TensorBoard**：可视化工具
+ **add_scalar()**
+ **add_image()**

```python
import numpy as np
from torch.utils.tensorboard import SummaryWriter
from PIL import Image

writer=SummaryWriter("logs")
img_path="练手数据集\\train\\ants_image\\0013035.jpg"
img_PIL=Image.open(img_path)
img_array=np.array(img_PIL)
# for i in range(100):
#     writer.add_scalar("y=2x",2*i,i)

writer.add_image("test",img_array,1,dataformats='HWC')
writer.close()
```

## transforms

```python
from torchvision import transforms
```

+ **totensor()**：将图片转为张量
+ **normalize()**：将图片归一化
+ **Compose()**：将多个转换组合
+ **Randomcrop()**：随机裁剪

```python
from PIL import Image
from torch.utils.tensorboard import SummaryWriter
from torchvision import transforms

writer=SummaryWriter("logs")
img_path=Image.open("data_set/train/ants/0013035.jpg")
print(img_path)

# ToTensor
trans_totensor=transforms.ToTensor()
img_tensor=trans_totensor(img_path)
writer.add_image("ToTensor",img_tensor,1)

# Normalize
trans_norm=transforms.Normalize([0.5,0.5,0.5],[0.5,0.5,0.5])
img_norm=trans_norm(img_tensor)
writer.add_image("Normalize",img_norm,1)

# Resize
trans_resize=transforms.Resize((512,512)) # 第一个是高第二个是宽
img_resize=trans_resize(img_path)
img_resize_PIL=trans_totensor(img_resize)
writer.add_image("Resize",img_resize_PIL,1)

# Compose
trans_resize_2=transforms.Resize(512) # 短边等于这个数值然后按比例缩放
trans_compose=transforms.Compose([trans_resize_2,trans_totensor])
img_resize_2=trans_compose(img_path)
writer.add_image("Resize",img_resize_2,1)

# RandomCrop
trans_random=transforms.RandomCrop(512)
trans_crop=transforms.Compose([trans_random,trans_totensor])
for i in range(10):
    img_crop=trans_crop(img_path)
    writer.add_image("RandomCrop",img_crop,i)

writer.close()
```
