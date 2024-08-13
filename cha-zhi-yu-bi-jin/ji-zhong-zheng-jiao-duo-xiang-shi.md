---
description: >-
  调用 cipy.special 库中的 legendre, chebyt, hermite, genlaguerre,
  jacobi函数，我们可以轻松实现对应阶数的正交多项式。
---

# 几种正交多项式

## 一、Legendre多项式

### 定义

<figure><img src="../.gitbook/assets/QianJianTec1723469409813.png" alt="" width="563"><figcaption></figcaption></figure>

是区间 \[ -1, 1 ] 上权函数<img src="../.gitbook/assets/image (3).png" alt="" data-size="line">( x ) = 1 的正交多项式且满足：

1.

    <figure><img src="../.gitbook/assets/QianJianTec1723469578148.png" alt="" width="563"><figcaption></figcaption></figure>
2. 有三项递推关系：

<figure><img src="../.gitbook/assets/QianJianTec1723469648079.png" alt="" width="563"><figcaption></figcaption></figure>

### 代码实现

```python
# 计算前 5 阶 Legendre 多项式
P = [legendre(n) for n in range(5)]
print('前 5 阶 Legendre 多项式：', P)
```

绘制图像以分别观察 3、10、50 阶的 Legendre 多项式

```python
# legendre
# 生成数据
x = np.linspace(-1, 1, 4)
legendre_poly = legendre(3)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, legendre_poly, label='Legendre Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('3rd Order Legendre Polynomial')
plt.legend()
plt.show()

# 生成数据
x = np.linspace(-1, 1, 11)
legendre_poly = legendre(10)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, legendre_poly, label='Legendre Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('10th Order Legendre Polynomial')
plt.legend()
plt.show()

# 生成数据
x = np.linspace(-1, 1, 51)
legendre_poly = legendre(50)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, legendre_poly, label='Legendre Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('50th Order Legendre Polynomial')
plt.legend()
plt.show()
```

## 二、Chebyshev多项式

### 定义

<figure><img src="../.gitbook/assets/QianJianTec1723470715289.png" alt="" width="563"><figcaption></figcaption></figure>

是区间 \[ -1, 1 ] 上权函数 <img src="../.gitbook/assets/QianJianTec1723470793418.png" alt="" data-size="line"> 的正交多项式，且满足:



*

    <figure><img src="../.gitbook/assets/QianJianTec1723470867575.png" alt=""><figcaption></figcaption></figure>
* 有三项递推关系：![](../.gitbook/assets/QianJianTec1723470936480.png)
* <img src="../.gitbook/assets/QianJianTec1723470991825.png" alt="" data-size="line"> 在 \[-1,1] 上的 n 个零点为：![](../.gitbook/assets/QianJianTec1723471018282.png)

### 代码实现

```python
# 计算前 5 阶 Chebyshev 多项式
T = [chebyt(n) for n in range(5)]
print('前 5 阶 Chebyshev 多项式：', T)
```

绘制图像以分别观察 3、10、50 阶的 Chebyshev 多项式

```python
# chebyt
# 生成数据
x = np.linspace(-1, 1, 4)
chebyt_poly = chebyt(3)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, chebyt_poly, label='Chebyt Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('3rd Order Chebyshev Polynomial')
plt.legend()
plt.show()

# 生成数据
x = np.linspace(-1, 1, 11)
chebyt_poly = chebyt(10)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, chebyt_poly, label='Chebyt Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('10th Order Chebyshev Polynomial')
plt.legend()
plt.show()

# 生成数据
x = np.linspace(-1, 1, 51)
chebyt_poly = chebyt(50)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, chebyt_poly, label='Chebyt Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('50th Order Chebyshev Polynomial')
plt.legend()
plt.show()
```

## 三、Laguerre多项式

### 定义

<figure><img src="../.gitbook/assets/QianJianTec1723471425412.png" alt="" width="563"><figcaption></figcaption></figure>

是区间 <img src="../.gitbook/assets/QianJianTec1723471515547.png" alt="" data-size="line"> 上权函数 <img src="../.gitbook/assets/QianJianTec1723471860972.png" alt="" data-size="line"> 的正交多项式，且满足：

*

    <figure><img src="../.gitbook/assets/QianJianTec1723471894937.png" alt="" width="563"><figcaption></figcaption></figure>
*   有三项递推关系：

    <figure><img src="../.gitbook/assets/QianJianTec1723471962609.png" alt="" width="375"><figcaption></figcaption></figure>

### 代码实现

```python
# 计算前 5 阶 (α=0) Laguerre 多项式
L = [genlaguerre(n, 0) for n in range(5)]
print('前 5 阶 Laguerre 多项式 (α=0) ：', L)
```

绘制图像以分别观察 3、10、50 阶的 Laguerre 多项式

```python
# Laguerre
# 生成数据
x = np.linspace(-1, 1, 4)
Laguerre_poly = genlaguerre(3, 0)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, Laguerre_poly, label='Laguerre Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('3rd Order Laguerre Polynomial')
plt.legend()
plt.show()

# 生成数据
x = np.linspace(-1, 1, 11)
Laguerre_poly = genlaguerre(10, 0)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, Laguerre_poly, label='Laguerre Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('10th Order Laguerre Polynomial')
plt.legend()
plt.show()

# 生成数据
x = np.linspace(-1, 1, 51)
Laguerre_poly = genlaguerre(50, 0)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, Laguerre_poly, label='Laguerre Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('50th Order Laguerre Polynomial')
plt.legend()
plt.show()
```

## 四、Hermite多项式

### 定义

<figure><img src="../.gitbook/assets/QianJianTec1723472258800.png" alt="" width="563"><figcaption></figcaption></figure>

是区间 <img src="../.gitbook/assets/QianJianTec1723472292079.png" alt="" data-size="line"> 上权函数 <img src="../.gitbook/assets/QianJianTec1723472318650.png" alt="" data-size="line"> 的正交多项式，且满足：

*

    <figure><img src="../.gitbook/assets/QianJianTec1723472363019.png" alt="" width="563"><figcaption></figcaption></figure>
*   有三项递推关系：

    <figure><img src="../.gitbook/assets/QianJianTec1723472401942.png" alt="" width="375"><figcaption></figcaption></figure>

### 代码实现

```python
# 计算 Hermite 多项式前 5 阶
H = [hermite(n) for n in range(5)]
print(H)
```

绘制图像以分别观察 3、10、50 阶的 Hermite 多项式

```python
# Hermite
# 生成数据
x = np.linspace(-1, 1, 4)
hermite_poly = hermite(3, 0)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, hermite_poly, label='Hermite Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('3rd Order Hermite Polynomial')
plt.legend()
plt.show()

# 生成数据
x = np.linspace(-1, 1, 11)
hermite_poly = hermite(10)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, hermite_poly, label='Hermite Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('10th Order Hermite Polynomial')
plt.legend()
plt.show()

# 生成数据
x = np.linspace(-1, 1, 51)
hermite_poly = hermite(50, 0)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, hermite_poly, label='Hermite Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('50th Order Hermite Polynomial')
plt.legend()
plt.show()
```

## 五、Jacobi多项式

### 定义

Jacobi 正交多项式 <img src="../.gitbook/assets/QianJianTec1723473292054.png" alt="" data-size="line"> 可以通过正交化代数多项式基底<img src="../.gitbook/assets/QianJianTec1723473345695.png" alt="" data-size="line">得到，这里的正交化是在内积空间<img src="../.gitbook/assets/QianJianTec1723473450332.png" alt="" data-size="line">中进行的。我们称<img src="../.gitbook/assets/QianJianTec1723473491021.png" alt="" data-size="line">为 n 次 Jacobi 多项式。

*

    <figure><img src="../.gitbook/assets/QianJianTec1723473530390.png" alt="" width="563"><figcaption></figcaption></figure>
*

    <figure><img src="../.gitbook/assets/QianJianTec1723473573494.png" alt="" width="563"><figcaption></figcaption></figure>
*

    <figure><img src="../.gitbook/assets/QianJianTec1723473605437.png" alt="" width="375"><figcaption></figcaption></figure>
*

    <figure><img src="../.gitbook/assets/QianJianTec1723473647137.png" alt=""><figcaption></figcaption></figure>

### 代码实现

```python
# 计算前 5 阶 (α=0.5, β=1.0) Jacobi 多项式
P = [jacobi(n, 0.5, 1.0) for n in range(5)]
print('前 5 阶 Jacobi 多项式 (α=0.5, β=1.0) ：', P)
```

绘制图像以分别观察 3、10、50 阶的 Jacobi 多项式

```python
# Jacobi
# 生成数据
x = np.linspace(-1, 1, 4)
jacobi_poly = jacobi(3, 0.5, 1.0)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, jacobi_poly, label='Jacobi Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('3rd Order Jacobi Polynomial')
plt.legend()
plt.show()

# 生成数据
x = np.linspace(-1, 1, 11)
jacobi_poly = jacobi(10, 0.5, 1.0)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, jacobi_poly, label='Jacobi Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('10th Order Jacobi Polynomial')
plt.legend()
plt.show()

# 生成数据
x = np.linspace(-1, 1, 51)
jacobi_poly = jacobi(50, 0.5, 1.0)
# 绘制图形
plt.figure(figsize=(8, 6))
plt.plot(x, jacobi_poly, label='Jacobi Polynomial')
plt.xlabel('x')
plt.ylabel('y')
plt.title('50th Order Jacobi Polynomial')
plt.legend()
plt.show()
```
