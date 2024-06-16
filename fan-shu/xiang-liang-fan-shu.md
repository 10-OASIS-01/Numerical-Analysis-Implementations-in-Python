# 向量范数

向量范数（Vector Norm）是数学中用来度量向量大小的一种工具。不同的范数对向量的各个分量进行不同的处理，从而反映向量在不同意义下的长度或大小。以下是一些常用的向量范数：

1. **L1范数（Manhattan Norm）**：
   * 定义：$$| \mathbf{x} |1 = \sum{i=1}^n |x_i|$$
   * 描述：L1范数是向量各个分量绝对值之和。
   * 应用：在稀疏表示、特征选择等领域中常用。
2. **L2范数（Euclidean Norm）**：
   * 定义：$$| \mathbf{x} |2 = \left( \sum{i=1}^n |x_i|^2 \right)^{1/2}$$
   * 描述：L2范数是向量各个分量平方和的平方根。
   * 应用：在几何学和物理中，L2范数是最常用的度量向量长度的方式。
3. **无穷范数（Infinity Norm）**：
   * 定义：$$| \mathbf{x} |_\infty = \max_i |x_i|$$
   * 描述：无穷范数是向量中分量绝对值的最大值。
   * 应用：在优化和误差分析中常用。
4. **p-范数**：
   * 定义：$$| \mathbf{x} |p = \left( \sum{i=1}^n |x_i|^p \right)^{1/p}$$
   * 描述：p-范数是向量各个分量绝对值的p次方和的1/p次方。
   * 应用：可以根据不同的p值调整度量方式，p取不同值会得到不同的范数。

#### 例子

设向量 $$\mathbf{x} = [x_1, x_2, \ldots, x_n]$$，以下是不同范数的计算示例：

* 对于向量$$\mathbf{x} = [1, -2, 3]$$：
  * L1范数：$$|\mathbf{x} |_1 = |1| + |-2| + |3| = 1 + 2 + 3 = 6$$
  * L2范数：$$| \mathbf{x} |_2 = \sqrt{1^2 + (-2)^2 + 3^2} = \sqrt{1 + 4 + 9} = \sqrt{14}$$
  * 无穷范数：$$| \mathbf{x} |_\infty = \max(|1|, |-2|, |3|) = 3$$

#### Python实现

可以使用NumPy库计算向量的不同范数：

```python
import numpy as np

x = np.array([1, -2, 3])

# L1范数
l1_norm = np.linalg.norm(x, ord=1)
print("L1 Norm:", l1_norm)

# L2范数
l2_norm = np.linalg.norm(x, ord=2)
print("L2 Norm:", l2_norm)

# 无穷范数
inf_norm = np.linalg.norm(x, ord=np.inf)
print("Infinity Norm:", inf_norm)

# p-范数（例如p=3）
p = 3
p_norm = np.linalg.norm(x, ord=p)
print(f"L{p} Norm:", p_norm)
```

#### 输出结果

```plaintext
L1 Norm: 6.0
L2 Norm: 3.7416573867739413
Infinity Norm: 3.0
L3 Norm: 3.3019272488946263
```

这些范数提供了度量向量大小的不同方式，根据具体应用场景的需求选择合适的范数来进行计算和分析。
