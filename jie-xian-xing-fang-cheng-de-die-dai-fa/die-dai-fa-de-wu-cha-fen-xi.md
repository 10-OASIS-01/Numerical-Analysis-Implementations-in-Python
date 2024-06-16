# 迭代法的误差分析

误差分析可以帮助我们理解迭代法的收敛速度和准确性。常见的误差指标包括：

*   **绝对误差**：当前解与真解之间的差距：

    $$
    e^{(k)} = x^{(k)} - x^*
    $$

    其中 $$x^*$$ 是线性方程组的真解。
*   **相对误差**：绝对误差与真解的比值：

    $$
    r^{(k)} = \frac{|e^{(k)}|}{|x^*|}
    $$
*   **残差**：当前解代入方程后的误差：

    $$
    r^{(k)} = b - Ax^{(k)}
    $$

在实际应用中，迭代法的误差分析通常结合数值实验，通过观测误差的收敛趋势来评估算法的性能。

#### 示例代码

```python
def compute_error(x, x_true):
    return np.linalg.norm(x - x_true)

def compute_relative_error(x, x_true):
    return np.linalg.norm(x - x_true) / np.linalg.norm(x_true)

def compute_residual(A, x, b):
    return np.linalg.norm(b - np.dot(A, x))
```

通过上述方法，我们可以实现并验证不同迭代法的效果，从而为实际问题的求解提供有效的数值工具。
