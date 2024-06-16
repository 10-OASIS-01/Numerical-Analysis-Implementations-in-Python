# Jacobi迭代法

Jacobi 迭代法是一种简单的迭代方法，用于求解线性方程组 $$Ax = b$$。其基本思想是将矩阵 $$A$$ 分解为对角矩阵 $$D$$ 和严格上三角矩阵 $$L + U$$：

$$
A = D + (L + U)
$$

Jacobi 迭代法的更新公式为：

$$
x^{(k+1)} = D^{-1}(b - (L + U)x^{(k)})
$$

算法步骤如下：

1. 初始化  $$x^{(0)}$$&#x20;
2. 对于 $$k = 0, 1, 2, \ldots$$ 重复以下步骤，直到满足停止准则：

$$
x_i^{(k+1)} = \frac{1}{a_{ii}} \left( b_i - \sum_{j \neq i} a_{ij} x_j^{(k)} \right)
$$

#### 实现代码

```python
import numpy as np

def jacobi(A, b, x0, tol=1e-10, max_iterations=1000):
    """
    Solve the system of linear equations Ax = b using the Jacobi iterative method.

    Parameters:
    A : numpy array
        Coefficient matrix
    b : numpy array
        Right-hand side vector
    x0 : numpy array
        Initial guess for the solution
    tol : float, optional
        Tolerance for convergence (default is 1e-10)
    max_iterations : int, optional
        Maximum number of iterations (default is 1000)

    Returns:
    x : numpy array
        Solution vector
    """
    D = np.diag(np.diag(A))
    R = A - D
    x = x0
    for _ in range(max_iterations):
        x_new = np.dot(np.linalg.inv(D), b - np.dot(R, x))
        if np.linalg.norm(x_new - x) < tol:
            return x_new
        x = x_new
    return x

# Example data
A = np.array([[4, 1, 2],
              [3, 5, 1],
              [1, 1, 3]])

b = np.array([4, 7, 3])

x0 = np.zeros(len(b))  # Initial guess

# Run Jacobi iterative method
solution = jacobi(A, b, x0)

print("Solution:", solution)

# Verify the result
print("Verification: A @ solution =", np.dot(A, solution))
print("b =", b)

```

