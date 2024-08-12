---
description: 在数值分析中，拉格朗日插值法是以法国十八世纪数学家约瑟夫·拉格朗日命名的一种多项式插值方法。
---

# Lagrange插值

## 定义：

<figure><img src="../.gitbook/assets/image (11).png" alt="" width="563"><figcaption></figcaption></figure>

称 ![](<../.gitbook/assets/image (13).png>) 为关于节点 ![](<../.gitbook/assets/image (14).png>) 的

<mark style="color:red;">n次Lagrange插值基函数</mark>，<img src="../.gitbook/assets/image (16).png" alt="" data-size="line"> 为<mark style="color:red;">n次Lagrange插值多项式</mark>。

其基函数为

<figure><img src="../.gitbook/assets/image (18).png" alt="" width="563"><figcaption></figcaption></figure>

将基函数代入即可求得n次Lagrange插值多项式，从而计算出对应节点的插值结果。

> Lagrange插值结构对称美观，可以利用离散数据获取插值函数，易于在计算机上实现。

### Lagrange插值余项（研究插值多项式的近似程度）：

<figure><img src="../.gitbook/assets/image (21).png" alt="" width="563"><figcaption></figcaption></figure>

其中 <img src="../.gitbook/assets/image (20).png" alt="" data-size="line"> 且与x有关。

## 优缺点分析：

<mark style="color:blue;">优点：</mark>结构紧凑，便于编程计算

<mark style="color:blue;">缺点：</mark>实际计算过程中，若需要增加节点，构造高次多项式时，必须全部重新计算，没有<mark style="color:red;">承袭性</mark>

## 代码实现：

```python
# Lagrange插值法
import numpy as np


def lagrange_interpolation(x, y, x_new):
    """
    Lagrange 线性插值

    输入:
    x - 已知的 x 坐标序列
    y - 已知的 y 坐标序列
    x_new - 需要计算插值的 x 坐标序列

    输出:
    y_new - 插值计算得到的 y 坐标序列
    """
    n = len(x)
    y_new = []

    for xn in x_new:
        # 计算每个插值点的 Lagrange 基函数
        L = [np.prod((xn - x[j]) / (x[i] - x[j])) for i in range(n) for j in range(n) if i != j]
        # 计算插值点的 y 坐标
        y_n = sum([y[i] * L[i] for i in range(n)])
        y_new.append(y_n)

    return y_new


# 示例使用
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]
x_new = [1.5, 2.7, 3.8, 4.2]
y_new = lagrange_interpolation(x, y, x_new)

print("插值后的 y 坐标序列:", y_new)
```
