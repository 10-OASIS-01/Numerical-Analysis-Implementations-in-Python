# 逐次超松弛迭代法（SOR 迭代法）

逐次超松弛迭代法（Successive Over-Relaxation, SOR）是 Gauss-Seidel 迭代法的进一步改进，通过引入松弛因子 $$\omega$$ 来加速收敛。其更新公式为：

$$
x_i^{(k+1)} = (1 - \omega) x_i^{(k)} + \frac{\omega}{a_{ii}} \left( b_i - \sum_{j=1}^{i-1} a_{ij} x_j^{(k+1)} - \sum_{j=i+1}^{n} a_{ij} x_j^{(k)} \right)
$$

算法步骤如下：

1. 初始化 $$x^{(0)}$$
2. 选择松弛因子 $$\omega$$
3. 对于 $$k = 0, 1, 2, \ldots$$ 重复以下步骤，直到满足停止准则：

$$
x_i^{(k+1)} = (1 - \omega) x_i^{(k)} + \frac{\omega}{a_{ii}} \left( b_i - \sum_{j=1}^{i-1} a_{ij} x_j^{(k+1)} - \sum_{j=i+1}^{n} a_{ij} x_j^{(k)} \right)
$$

#### 实现代码

```python
import numpy as np

def gauss_seidel_sor(A, b, x0, omega, tol=1e-10, max_iterations=1000):
    """
    Solve the system of linear equations Ax = b using the Gauss-Seidel method with SOR.

    Parameters:
    A : numpy array
        Coefficient matrix
    b : numpy array
        Right-hand side vector
    x0 : numpy array
        Initial guess for the solution
    omega : float
        Relaxation parameter (0 < omega < 2)
    tol : float, optional
        Tolerance for convergence (default is 1e-10)
    max_iterations : int, optional
        Maximum number of iterations (default is 1000)

    Returns:
    x : numpy array
        Solution vector
    """
    n = len(b)
    if len(x0) != n:
        raise ValueError("Initial guess x0 must have the same length as vector b.")

    x = x0
    for _ in range(max_iterations):
        x_new = np.copy(x)
        for i in range(n):
            sum1 = np.dot(A[i, :i], x_new[:i])
            sum2 = np.dot(A[i, i + 1:], x[i + 1:])
            x_new[i] = (1 - omega) * x[i] + (omega / A[i, i]) * (b[i] - sum1 - sum2)
        if np.linalg.norm(x_new - x) < tol:
            return x_new
        x = x_new

    raise RuntimeError("SOR method did not converge within the specified number of iterations.")

# Example usage
A = np.array([[4, -1, 0, 0],
              [-1, 4, -1, 0],
              [0, -1, 4, -1],
              [0, 0, -1, 3]])

b = np.array([0, 5, 0, 5])

x0 = np.zeros(len(b))  # Initial guess
omega = 1.2  # Relaxation parameter

# Solve using Gauss-Seidel with SOR
solution = gauss_seidel_sor(A, b, x0, omega)

print("Solution:", solution)

# Verification
print("Verification: A @ solution =", np.dot(A, solution))
print("b =", b)

```
