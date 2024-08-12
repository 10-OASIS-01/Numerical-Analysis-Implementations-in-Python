# Newton迭代法的变形

牛顿迭代法是一种求解方程 f(x) = 0 的经典数值方法，它利用了目标函数在某点的导数信息来快速逼近根。然而，对于某些特殊的目标函数，标准的牛顿迭代法可能会出现收敛性问题或无法达到理想的收敛速度等。为了解决这些问题，数值分析领域提出了一些牛顿迭代法的变形算法，下面简单介绍几种：

## 一、简化Newton迭代法

### 核心思想：使用初值x0处的导数值代替导数表达式

迭代格式：

<figure><img src="../.gitbook/assets/QianJianTec1722600052814 (1).jpg" alt="" width="563"><figcaption></figcaption></figure>

通常取

<figure><img src="../.gitbook/assets/image (1) (1).png" alt="" width="144"><figcaption></figcaption></figure>

当满足 <img src="../.gitbook/assets/image (2) (1).png" alt="" data-size="original"> 时，简化Newton迭代法对于精确解的邻域收敛。

简化Newton迭代法通常只有<mark style="color:red;">线性收敛</mark>！

## 二、割线法

### 核心思想：用割线斜率近似切线斜率，即免去计算 f ( x ) 的导数表达式

即：![](<../.gitbook/assets/image (3) (1).png>)

迭代格式：

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

## 三、带参数m的Newton迭代法

设 x\* 是 f ( x ) = 0 的 m 重根，则 ![](<../.gitbook/assets/image (5) (1).png>)

其中 h ( x ) 在 x = x\* 处连续，且 h ( x\* ) 不为 0 .

若令  ![](<../.gitbook/assets/image (6).png>) ，则 x\* 恰为 F ( x ) = 0 的单根。

由牛顿迭代法可得：

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

此式称为带参数m的Newton迭代法，它是求方程 f ( x ) = 0 的 m 重根的具有平方收敛的迭代法。

<mark style="color:red;">缺点</mark>：方程的根的重数 m 通常是未知的。

### 改进：

已知 x\* 是方程 f ( x ) = 0 的 m 重根，则 x\* 是方程

<figure><img src="../.gitbook/assets/image (8).png" alt="" width="375"><figcaption></figcaption></figure>

的 m - 1 重根，所以令

<figure><img src="../.gitbook/assets/image (9).png" alt="" width="375"><figcaption></figcaption></figure>

则 x\* 恰是方程 u ( x ) = 0 的单根，此时再使用牛顿迭代法有：

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

这是求方程 f ( x ) = 0 重根的具有平方收敛的迭代法，而且<mark style="color:red;">无需知道根的重数</mark>！
