# 二分法

**基本思想**： 先利用<mark style="color:blue;">零点定理</mark>确定根的存在区间，然后将含根 α 的区间对半分开（即二分法名字由来），通过判别中点函数值的符号，将有根区间缩小；重复以上过程，直至根的存在区间缩小到充分小，即可求出满足所给精度要求的根的<mark style="color:blue;">近似值</mark>。

## 解题步骤：

给定精确度 ε ，用二分法求解 f(x) 零点近似值：

1. 确定有根区间 \[a, b] ，验证 f(a)\* f(b) < 0 ，给定精确度 ε ；
2. 求有根区间 \[a, b] 的中点 c ；
3. 计算 f(c) ：
   1. 若 f(c) = 0 ， 则 c 为函数零点；
   2. 若 f(c) < 0 ，则令 b = c ，确定新的有根区间；
   3. 若 f(c) > 0 ，则令 a = c ，确定新的有根区间；
4. 判断是否达到精确度 ε ：若 | b < a | < ε ，即得到零点近似值 a (或 b )；否则，重复2\~4直至足够精确。

二分法的优点是方法和计算都简单，且对函数 f(x) 的性质要求不高，只需连续即可；而其缺点是收敛速度慢，也不能求偶数重根。&#x20;

## 使用Python模拟：

```python
# 二分法

def f(x):
    return x**3 - 2*x + 1


def bisection(f, a, b, tol):
    """
    使用二分法求函数f(x)在区间[a, b]上的零点近似值。

    参数:
    f (function): 要求解零点的函数
    a (float): 区间左端点
    b (float): 区间右端点
    tol (float): 精度要求

    返回:
    float: 函数零点的近似值
    """
    if f(a) * f(b) >= 0:
        print("在给定区间内没有零点或有多个零点，此时二分法不适用！")
        return None

    c = a
    while abs(b - a) >= tol:
        c = (a + b) / 2
        if f(c) == 0:
            break
        elif f(a) * f(c) < 0:
            b = c
        else:
            a = c
    return c


# 生成数据
a = -2
b = 2
tol = 1e-6

# 求解零点
root = bisection(f, a, b, tol)

if root is not None:
    print(f"函数f(x)在区间[{a}, {b}]上的零点近似值为: {root}")
else:
    print("无法找到函数的零点")
```

此代码实现了对于二分法的简单模拟，读者使用时根据实际情况更改 f(x) 、a 、b 、以及 ε 的值即可。
