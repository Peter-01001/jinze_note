# pytorch

## numpy

Numpy 是 Python 处理数值数组的核心库，PyTorch 张量的操作几乎和 Numpy 一致，先学最核心的数组操作。

### 导入numpy库

    import numpy as np

### 创建numpy数组

    arr1 = np.array([[1, 2], [3, 4]])  # 2行2列的二维数组
    arr2 = np.ones((2, 2))             # 全1数组（和torch.ones一致）

+ np.array()接收Python
列表作为参数，生成NumPy数组

### 数组形状

    作为数组方法
    arr_2x3 = arr.reshape(2, 3)      # shape: (2, 3)
    arr_flat = arr.reshape(-1)       # 展平为一维
    加上copy则为复制

### 数组运算

      print(arr1 + arr2)  # 逐元素相加：[[2,3],[4,5]]
      print(arr1 @ arr2)  # 矩阵乘法（和torch.matmul一致）

## tensor操作

### 张量：张量，多维数组

+ 0 维张量：单个数字（如 5）→ 标量
+ 1 维张量：[1,2,3] → 向量（比如一个人的身高、体重、年龄）
+ 2 维张量：\[[1,2],[3,4]] → 矩阵（比如 100 个样本，每个样本 2 个特征）

+ **创建tensor**：

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
