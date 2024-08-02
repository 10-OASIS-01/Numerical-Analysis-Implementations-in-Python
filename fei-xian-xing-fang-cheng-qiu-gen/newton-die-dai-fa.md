# Newton迭代法

### 原理：将非线性方程线性化

#### 收敛速度：Newton 迭代法在单根处至少具有二阶收敛性，但 Newton 迭代法一般只有局部收敛性。

注意：Newton迭代法对于<mark style="color:blue;">初值x0</mark>要求较为严苛！

## 迭代公式：

<figure><img src="../.gitbook/assets/QianJianTec1722570349235.jpg" alt="" width="375"><figcaption></figcaption></figure>

## 代码实现：

```python
import numpy as np
import matplotlib.pyplot as plt

def f(x):
    return x**2 - 2

def df(x):
    return 2 * x

def newton_method(f, df, x0, tol=1e-10, max_iter=100):
    x = x0
    iterations = [x0]
    
    for _ in range(max_iter):
        x_new = x - f(x) / df(x)
        iterations.append(x_new)
        if abs(x_new - x) < tol:
            break
        x = x_new
    
    return x, iterations

# 初始猜测
x0 = 1.0

# 使用牛顿迭代法求解
root, iterations = newton_method(f, df, x0)

print(f"Approximate root: {root}")
```

同样，我们可以画出迭代的根的折线图，更直观地观察其迭代情况：

```python
# 绘制迭代过程
plt.plot(iterations, marker='o')
plt.xlabel('Iteration')
plt.ylabel('x')
plt.title('Newton Method Convergence')
plt.grid(True)
plt.show()
```
