# 简单迭代法的收敛条件

## 定义：

若存在常数 L > 0 ，使&#x20;

$$
| g ( x 1 ) − g ( x 2 ) | ⩽ L ∣ x 1 − x 2 ∣，∀x 1 ​ , x 2 ​ ∈[a,b]
$$

则称函数 g ( x ) 在 \[ a , b ] 满足 <mark style="color:blue;">Lipschitz 条件</mark>，L 称为 Lipschitz 常数。

常取

$$
L = max ⁡| g ′ ( x ) |  ,       x ∈ [ a , b ]
$$

并用 ∣g′( x )∣< 1  来判断迭代公式是否收敛。

## 实现代码：

```python
import numpy as np
import matplotlib.pyplot as plt

def g(x):
    return 0.5 * (x + 2 / x)

def is_lipschitz(g, a, b, num_points=1000):
    x = np.linspace(a, b, num_points)
    max_lipschitz_constant = 0
    
    for i in range(num_points):
        for j in range(i + 1, num_points):
            x_i = x[i]
            x_j = x[j]
            if x_i != x_j:
                lipschitz_constant = abs(g(x_i) - g(x_j)) / abs(x_i - x_j)
                max_lipschitz_constant = max(max_lipschitz_constant, lipschitz_constant)
    
    return max_lipschitz_constant

# 设置区间 [a, b]
a, b = 0.5, 2.0

# 验证利普希兹条件
L = is_lipschitz(g, a, b)
print(f"Lipschitz constant: {L}")
if L < 1:
    print("The iteration method is convergent.")
else:
    print("The iteration method is not convergent.")
```

我们可以继续对于迭代法进行模拟，观察其收敛情况：

```python
# 迭代法模拟
x0 = 1.0
iterations = [x0]
for _ in range(10):
    x0 = g(x0)
    iterations.append(x0)

# 绘制迭代过程
plt.plot(iterations, marker='o')
plt.xlabel('Iteration')
plt.ylabel('x')
plt.title('Iteration Method Convergence')
plt.grid(True)
plt.show()
```

可以看出，在上文选定的 \[ 0.5, 2.0 ] 区间上，确实是不收敛的。
