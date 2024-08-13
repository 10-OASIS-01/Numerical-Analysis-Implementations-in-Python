# Newton插值

## 定义：

### 差商的定义：

一阶差商：

![](<../.gitbook/assets/image (1) (1) (1).png>)

二阶差商：

![](<../.gitbook/assets/image (1) (1) (1) (1).png>)

k阶差商：

<figure><img src="../.gitbook/assets/image (2) (1).png" alt="" width="563"><figcaption></figcaption></figure>

<mark style="color:blue;">注：在以上定义中，点x0，x1，...，xk为互不相同的点。</mark>

### 差商的性质：

利用该性质可直接求出特定的差商，简化计算过程！

若 f (x) 具有 k 阶连续导数，则

<figure><img src="../.gitbook/assets/image (3) (1).png" alt="" width="364"><figcaption></figcaption></figure>

其中 <img src="../.gitbook/assets/image (4).png" alt="" data-size="line"> 在 k+1 个节点之间。

### 差商表：

实际计算中，常常列出如下的差商表并计算：

<figure><img src="../.gitbook/assets/QianJianTec1723207046958.png" alt=""><figcaption></figcaption></figure>

### Newton插值的定义：

<figure><img src="../.gitbook/assets/QianJianTec1723209058715.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/QianJianTec1723209093127 (1).png" alt="" width="563"><figcaption></figcaption></figure>

称 Nn( x ) 为 <mark style="color:red;">n 次 Newton 插值多项式</mark>，Rn( x ) 为 <mark style="color:red;">n 次 Newton 插值余项</mark>。

### Newton插值的<mark style="color:blue;">承袭性</mark>：

<figure><img src="../.gitbook/assets/QianJianTec1723209311610.png" alt=""><figcaption></figcaption></figure>

该性质大大减少了增加节点时的计算量，十分重要。

## 代码实现：

求 n 阶差商：

```python
# n阶差商
def diff(xi, yi, n):
    """
    参数：
    param xi:插值节点xi
    param yi:插值节点yi
    param n: n阶

    返回：
    return: n阶差商
    """
    if len(xi) != len(yi):  # xi和yi数量须一致
        return
    else:
        diff_quot = [[] for i in range(n)]  # j为列，i为行！
        for j in range(1, n+1):
            if j == 1:  # 计算一阶差商
                for i in range(n+1-j):
                    diff_quot[j-1].append((yi[i+1]-yi[i]) / (xi[i+1] - xi[i]))
            else:  # 计算n阶差商
                for i in range(n+1-j):
                    diff_quot[j-1].append((diff_quot[j-2][i+1]-diff_quot[j-2][i]) / (xi[i+j] - xi[i]))
        return diff_quot

# 举例
xi = [-2, -1, 1, 2]
yi = [5, 3, 17, 21]
n = 3
print(diff(xi, yi, n))

```

Newton插值完整代码：

```python
# Newton插值
def diff(xi, yi, n, x):
    """
    参数：
    param xi:插值节点xi
    param yi:插值节点yi
    param n: n阶
    param x: 近似值
    返回：
    return: n阶差商
    """
    if len(xi) != len(yi):  # xi和yi数量须一致
        return
    else:
        diff_quot = [[] for i in range(n)]  # j为列，i为行！
        for j in range(1, n+1):
            if j == 1:  # 计算一阶差商
                for i in range(n+1-j):
                    diff_quot[j-1].append((yi[i+1]-yi[i]) / (xi[i+1] - xi[i]))
            else:  # 计算n阶差商
                for i in range(n+1-j):
                    diff_quot[j-1].append((diff_quot[j-2][i+1]-diff_quot[j-2][i]) / (xi[i+j] - xi[i]))
    newton = yi[0]
    v = []  # 存储连乘rou
    rou = 1
    for i in range(n):
        rou *= (x - xi[i])
        v.append(rou)
        newton += diff_quot[i][0] * v[i]
    return newton


xi = [-2, -1, 1, 2]
yi = [5, 3, 17, 21]
n = 3
x = 0.3
print(diff(xi, yi, n, x))
```
