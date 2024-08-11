# Hermite插值

## Runge现象

在数值分析领域中，龙格现象是在一组等间插值点上使用具有高次多项式的多项式插值时出现的<mark style="color:red;">区间边缘处的振荡问题</mark>。（如下图，来自维基百科）

<figure><img src="../.gitbook/assets/image (22).png" alt="" width="525"><figcaption></figcaption></figure>

它表明**使用高次多项式插值并不总能提高准确性**，相反，容易产生过度拟合，偏离原函数。

事实上，我们很少采用高于7次的插值多项式。为了解决这个问题，我们引入了分段插值的概念，本节着重介绍Hermite插值。

## Hermite插值

### 定义

在节点处给出如下插值条件：

<figure><img src="../.gitbook/assets/QianJianTec1723259405995.png" alt="" width="563"><figcaption></figcaption></figure>

根据该条件构造基函数，通过基函数法进行求解：

下面列出所符合的条件

<figure><img src="../.gitbook/assets/QianJianTec1723260086628 (1).png" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/QianJianTec1723260374507.png" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/QianJianTec1723260470376.png" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/QianJianTec1723282276718.png" alt="" width="563"><figcaption></figcaption></figure>

通过代数运算可求得如下结果：

<figure><img src="../.gitbook/assets/QianJianTec1723282566325.png" alt="" width="375"><figcaption></figcaption></figure>



所求的插值多项式如下：



<figure><img src="../.gitbook/assets/QianJianTec1723282511989.png" alt="" width="563"><figcaption></figcaption></figure>

根据上述内容，使用python编码实现即可。

### 代码实现

```python
# Hermite插值
import numpy as np
import matplotlib.pyplot as plt


def f(x):  # 函数
    return np.exp(x)
    
    
def df(x):  # 导数
    return np.exp(x)
    
    
def H3(x, x0, x1, f0, f1, df0, df1):  # 定义两点三次 Hermite 插值函数
    return (f0 * (1 + 2 * (x - x0) / (x1 - x0)) + df0 * (x - x0)) * ((x - x1) / (x0 - x1)) ** 2 + (
                f1 * (1 + 2 * (x - x1) / (x0 - x1)) + df1 * (x - x1)) * ((x - x0) / (x1 - x0)) ** 2


# 插值区间
a = -4
b = 4
N = [1, 2, 3, 5, 8]
k = 0
for n in N:
    h = (b - a) / n  # 步长
    xi = np.linspace(a, b, n + 1)  # 插值节点
    fi = f(xi)  # 对应函数值
    dfi = df(xi)  # 一阶导数值
    x = np.linspace(a, b, 10)
    L = len(x)
    y = np.zeros((L, 1))
    for j in range(0, L):
        for k in range(0, n + 1):
            if k < n + 1 and xi[k + 1] >= x[j]:  # 使用与目标值最接近的两点进行插值计算！
                break
        y[j] = H3(x[j], xi[k], xi[k + 1], fi[k], fi[k + 1], dfi[k], dfi[k + 1])
    plt.plot(x, f(x))
    plt.plot(x, y)
    plt.title('n=%d' % n)
    plt.legend(['f(x)', 'H3(x)'])
    plt.xlabel('x label')
    plt.ylabel('y label')
    plt.show()
```



































