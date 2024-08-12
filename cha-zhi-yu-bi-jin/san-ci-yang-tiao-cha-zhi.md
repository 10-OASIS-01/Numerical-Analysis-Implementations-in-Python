# 三次样条插值

## 引入

在设计室，为了保证设计的规范要求，必须使得特定的函数具有连续的 n 阶导数，保证曲线的曲率变化的连续。常用的通常包括线性、二次和三次样条插值函数，它们被广泛地应该用于观测数据的处理和船舶、汽车、飞机的外形设计。

## 定义

### 函数

给定节点![](<../.gitbook/assets/image (23).png>)，及其上的函数值![](<../.gitbook/assets/image (24).png>)，如果函数 S ( x ) 满足：

（1） S ( x ) 是一个分段的三次多项式且 S ( x ) = yk；

（2）<img src="../.gitbook/assets/image (25).png" alt="" data-size="line">.

则称 S ( x ) 是区间 \[ a, b ] 上的<mark style="color:red;">三次样条插值函数</mark>。

### 边界条件

正常计算的过程中共有 4n 个待定系数需要确定，而一般能获取 4n - 2 的条件。为了获得唯一的三次样条函数，通常会在区间 \[ a, b ] 的端点 x0 = a ，xn = b 上各加一个条件，称为<mark style="color:red;">边界条件</mark>。常用的边界条件有：

（1）![](../.gitbook/assets/QianJianTec1723366573368.png)

（2）![](../.gitbook/assets/QianJianTec1723366638412.png)

（3）假设 f ( x ) 是以 b - a 为周期的周期函数，这时要求

<figure><img src="../.gitbook/assets/QianJianTec1723366855525.png" alt="" width="188"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/QianJianTec1723366828991.png" alt="" width="188"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/QianJianTec1723366769932.png" alt="" width="188"><figcaption></figcaption></figure>

这样确定的 S ( x ) 为<mark style="color:red;">周期样条函数</mark>。

## 代码实现

这里我们采用了已经封装好的 `scipy.interpolate` 库中的 `CubicSpline` 直接实现

```python
# 样条插值
import numpy as np
from scipy.interpolate import CubicSpline
import matplotlib.pyplot as plt

# 1、自然边界条件,即在边界点处一阶导数为 0
# 定义数据点
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 4, 2]
# 创建三次样条插值对象
cs = CubicSpline(x, y)
# 生成插值结果
x_new = np.linspace(1, 5, 100)
y_new = cs(x_new)
# 绘制插值曲线
plt.figure(figsize=(8, 6))
plt.plot(x, y, 'o', label='Data points')
plt.plot(x_new, y_new, label='Cubic spline interpolation')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Natural Boundary Condition')
plt.legend()
plt.grid()
plt.show()

# 2、周期边界条件,即在边界点处一阶导数连续
# 定义数据点
x = np.array([1, 2, 3, 4, 5])
y = np.array([2.8, 4, -3.2, 4, 2.8])
# 创建三次样条插值对象,设置为周期边界条件
cs = CubicSpline(x, y, bc_type='periodic')
# 生成插值结果
x_new = np.linspace(1, 5, 100)
y_new = cs(x_new)
# 绘制插值曲线
plt.figure(figsize=(8, 6))
plt.plot(x, y, 'o', label='Data points')
plt.plot(x_new, y_new, label='Periodic cubic spline interpolation')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Periodic Boundary Condition')
plt.legend()
plt.grid()
plt.show()

# 3、固定边界条件,即在边界点处一阶导数等于给定值 (这里设置为 -2 3)
# 定义数据点
x = np.array([1, 2, 3, 4, 5])
y = np.array([4.8, 0.2, -3.2, 4, 1.8])
# 创建三次样条插值对象,设置为固定边界条件
cs = CubicSpline(x, y, bc_type=((1, -2), (1, 3)))
# 生成插值结果
x_new = np.linspace(1, 5, 100)
y_new = cs(x_new)
# 绘制插值曲线
plt.figure(figsize=(8, 6))
plt.plot(x, y, 'o', label='Data points')
plt.plot(x_new, y_new, label='Clamped cubic spline interpolation')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Clamped Boundary Condition')
plt.legend()
plt.grid()
plt.show()
```

在 Python 的 `scipy.interpolate.CubicSpline` 中，无法直接设置二阶导数作为边界条件，所以我们把相应的实现方法依照该库改成了：自然边界条件、周期边界条件、固定边界条件三种，请读者注意区分。
