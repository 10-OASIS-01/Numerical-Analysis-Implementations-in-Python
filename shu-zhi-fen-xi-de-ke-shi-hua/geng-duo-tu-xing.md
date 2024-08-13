# 更多图形

## 一、热力图

### 定义与使用场景

热力图 ( Heatmap ) 是一种二维数据可视化方式，它使用颜色的深浅来表示数据矩阵中每个单元格的数值大小。

热力图的基本原理是将数据矩阵中的每个值映射到一个特定的颜色，通常从低值的淡色到高值的深色。这种直观的视觉表达方式，使热力图能够有效地展示数据在二维平面上的分布情况和密集程度。

热力图的主要使用场景：

1. **数据分布分析**
   * 热力图能够帮助用户快速发现数据在二维平面上的集中区域和稀疏区域，识别数据中的"热点"。
   * 常用于分析地理数据、销售数据、人口密度等二维数据。
2. **相关性分析**
   * 热力图可用于显示两个变量之间的相关性强度，通过颜色深浅直观地展示变量间的关联程度。
   * 广泛应用于数据分析、机器学习等领域中的特征相关性分析。
3. **异常检测**
   * 热力图可以帮助发现数据中的异常点或异常区域，为异常值检测提供可视化支持。
   * 在监控、质量控制等场景中，热力图可用于辅助异常数据的发现。
4. **数据探索和可视化**
   * 热力图是一种简单直观的数据可视化方式，能够帮助用户更好地理解和探索二维数据的整体分布特征。
   * 广泛应用于数据分析、商业智能、生物信息学等领域的数据可视化中。

### 代码示例

```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
# 生成示例数据
np.random.seed(24)
data = np.random.normal(0, 1, (10, 10))
# 创建热力图
plt.figure(figsize=(10, 8))
sns.heatmap(data, cmap='viridis', annot=True, fmt='.2f')
# 设置标题和坐标轴标签
plt.title('Heatmap Example')
plt.xlabel('X')
plt.ylabel('Y')
plt.show()
```

## 二、3D 线框图

### 定义与使用场景

3D 线框图 ( 3D Wireframe Plot ) 是一种三维数据可视化方法，它使用网格状的线条来表示数据在三维空间中的分布情况。

具体来说，3D 线框图会在三维坐标系中绘制一个由线条组成的网格,每个交叉点的位置和高度都对应着数据集中的一个数值。这样，线框图就能够直观地展示数据在三维空间中的变化情况。

3D 线框图的主要使用场景包括

1. **科学和工程数据可视化**
   * 3D 线框图常用于展示各种物理、化学、工程等领域中的三维数据，如温度场、压力场、应力分布等。
   * 这种可视化方式能够帮助研究人员更好地理解和分析三维数据的特征。
2. **地理信息系统 ( GIS )**
   * 在地理信息系统中，3D 线框图可用于表示地形、地貌、海底地形等三维空间数据。
   * 这种可视化方式有助于分析地理空间数据的特征，为规划、决策提供支持。
3. **医学影像分析**
   * 3D 线框图可用于显示医学成像数据，如CT、MRI等扫描图像中的三维结构。
   * 这种可视化有助于医生更好地理解人体结构，为诊断和手术规划提供参考。

### 代码示例

```python
import numpy as np
import matplotlib.pyplot as plt

# 生成3D数据
x = np.arange(-4, 4, 0.25)
y = np.arange(-4, 4, 0.25)
X, Y = np.meshgrid(x, y)
Z = np.sin(np.sqrt(X**2 + Y**2))

# 创建3D线框图
fig = plt.figure(figsize=(10, 8))
ax = fig.add_subplot(111, projection='3d')
ax.plot_wireframe(X, Y, Z, color='b')

# 设置标题、标签和视角
ax.set_title('3D Wireframe Plot')
ax.set_xlabel('X')
ax.set_ylabel('Y')
ax.set_zlabel('Z')
ax.view_init(30, 45)
plt.show()
```

## 三、3D 散点图

### 定义与使用场景

3D 散点图是一种常用的三维数据可视化方式，它能够直观地展示数据点在三维空间中的分布情况。

3D 散点图的主要使用场景包括

1. **多变量关系分析**
   * 3D 散点图可以同时展示三个变量之间的关系，有助于发现隐藏的模式和异常。
   * 在科学研究、数据挖掘等领域广泛应用。
2. **聚类分析**
   * 3D 散点图可用于可视化高维数据的聚类情况，帮助识别数据中的自然分组。
3. **空间数据可视化**
   * 3D 散点图适用于展示位于三维空间中的数据，如地理位置数据、医疗影像数据等。

### 代码示例

<pre class="language-python"><code class="lang-python">import numpy as np
import matplotlib.pyplot as plt

<strong># 生成3D随机数据
</strong>np.random.seed(24)
x = np.random.normal(0, 1, 100)
y = np.random.normal(0, 1, 100)
z = np.random.normal(0, 1, 100)

# 创建3D散点图
fig = plt.figure(figsize=(10, 8))
ax = fig.add_subplot(111, projection='3d')
ax.scatter(x, y, z, c='b', marker='o')

# 设置标题、标签和视角
ax.set_title('3D Scatter Plot')
ax.set_xlabel('X')
ax.set_ylabel('Y')
ax.set_zlabel('Z')
ax.view_init(30, 45)

plt.show()
</code></pre>

## 四、3D 曲面图

### 定义和使用场景

3D 曲面图是一种常用的三维数据可视化方式，它能够清楚地展示数据在三维空间中的分布和变化情况。

3D 曲面图的主要使用场景包括

1. **科学和工程数据可视化**
   * 同上述的 3D 散点图，3D 曲面图常用于可视化各种物理、化学、工程等领域中的三维数据，如温度场、压力场、应力分布等，可帮助理解和分析三维数据的特征。
2. **地理信息系统 ( GIS )**
   * 在地理信息系统中，3D 曲面图可用于表示地形、地貌、海底地形等三维空间数据。
   * 这种可视化方式有助于分析地理空间数据的特征，为规划、决策提供支持。

### 代码示例

```python
import numpy as np
import matplotlib.pyplot as plt

# 生成3D数据
x = np.arange(-4, 4, 0.25)
y = np.arange(-4, 4, 0.25)
X, Y = np.meshgrid(x, y)
Z = np.sin(np.sqrt(X**2 + Y**2))

# 创建3D曲面图
fig = plt.figure(figsize=(10, 8))
ax = fig.add_subplot(111, projection='3d')
ax.plot_surface(X, Y, Z, rstride=1, cstride=1, cmap='viridis')

# 设置标题、标签和视角
ax.set_title('3D Surface Plot')
ax.set_xlabel('X')
ax.set_ylabel('Y')
ax.set_zlabel('Z')
ax.view_init(30, 45)

plt.show()
```
