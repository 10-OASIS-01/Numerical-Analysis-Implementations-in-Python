# 普通图形

准备工作：导入相关库

```python
import matplotlib.pyplot as plt
import numpy as np
```

## 一、散点图

散点图(Scatter Plot)是一种常见的数据可视化方式，它主要用于展示两个变量之间的关系。

散点图的特点是利用二维平面上的点的位置来表示两个变量之间的关系，点的位置由两个变量的值决定。通过观察点在平面上的分布情况，可以直观地判断出变量之间是否存在线性相关、是否存在异常值或异常分布，以及变量之间的相关强度等信息。

散点图适用于展示连续型变量之间的关系，是一种非常直观和有效的数据分析工具。在各个领域，散点图广泛应用于变量关系探索、相关性分析、异常值检测、趋势预测等场景，帮助用户快速发现数据中隐藏的模式和规律。

下面是一个简单示例：

```python
# 准备数据
x = np.random.normal(0, 1, 50)
y = np.random.normal(0, 1, 50)
# 创建散点图
plt.figure(figsize=(8, 6))
plt.scatter(x, y)
# 设置标题、标签
plt.title('Scatter Plot Example')
plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.show()
```

## 二、折线图

折线图(Line Chart)是一种常见的时间序列数据可视化方式，它主要用于展示一个或多个变量随时间变化的趋势。

折线图利用折线的形状来表示变量随时间的变化情况，能够直观地显示数据的变化趋势、峰值和波动情况。

折线图适用于连续型时间序列数据，如股票价格、产品销量、网站访问量等，可以帮助用户快速洞察数据随时间的变化规律。通过在同一图表上绘制多条折线，折线图还能够比较不同变量或指标的变化情况,发现它们之间的相关性。

此外，折线图易于理解，常被用于业务报告、市场分析、数据仪表盘等场景，帮助决策者准确把握数据变化的走势，及时发现问题并做出决策。

下面是一个简单示例：

```python
# 准备数据
x = np.arange(1, 11)
data1 = [6, 3.8, 4.4, 6, 6.5, 5.6, 7.2, 4.1, 5.8, 8.4]
data2 = [7, 6, 8, 7, 8, 6, 9, 7, 8, 7]
# 创建折线图
plt.figure(figsize=(8, 6))
plt.plot(x, data1, label='Data 1', marker='o', linewidth=3)
plt.plot(x, data2, label='Data 2', marker='o', linewidth=3, linestyle='--')
# 设置标题、标签和图例
plt.title('Line Chart Example')
plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.legend()
plt.grid(True)
plt.show()
```

## 三、条形图

条形图(Bar Chart)是一种常见的数据可视化方式，它主要用于直观展示和比较不同类别之间的数值差异。

条形图使用水平或垂直的条形来表示不同类别的数值大小，条形的长度与数值大小成正比。这种直观的视觉表达方式，使条形图能够有效地比较不同类别之间的数值差异。

条形图适用于离散型或分类型数据，如产品销量、地区收入、员工绩效等，可以帮助用户快速识别数据中的突出趋势和异常情况。

此外，条形图还可以用于展示单个类别随时间变化的数值走势或对比同一类别在不同维度(如地区、部门等)的表现。作为一种简单易懂的数据可视化工具，条形图广泛应用于业务报告、绩效分析、市场调研等领域，为使用者提供直观清晰的数据支持。

下面是一个简单示例：

```python
# 准备数据
labels = ['A', 'B', 'C', 'D', 'E']
data1 = [10, 15, 12, 8, 18]
data2 = [8, 12, 10, 14, 15]
data3 = [12, 11, 15, 9, 13]
x = np.arange(len(labels))  # 获取x轴刻度的位置
width = 0.2  # 设置每个条形的宽度
# 创建并排的条形图
plt.figure(figsize=(10, 6))
plt.bar(x - width, data1, width, label='Data 1')
plt.bar(x, data2, width, label='Data 2')
plt.bar(x + width, data3, width, label='Data 3')
# 设置标题、标签和图例
plt.xticks(x, labels)
plt.title('Grouped Bar Chart Example')
plt.xlabel('Category')
plt.ylabel('Value')
plt.legend()
plt.show()
```

## 四、饼状图

饼状图(Pie Chart)也是一种常见的数据可视化方式，它主要用于直观地展示一个整体被划分为不同部分的比例关系。

饼状图将一个整体(通常表示为100%)划分为多个扇形区域，每个扇形代表一个类别或部分,其面积大小与该类别在总体中所占的比例相对应。这种直观的圆形表达方式，使饼状图能够清晰地展示数据的构成情况和各部分之间的相对大小关系。

饼状图适用于展示部分与整体之间的比例数据，如销售占比、支出结构、市场份额等，能够帮助观察者快速理解数据的组成情况。

下面是一个简单示例：

```python
# 准备数据
labels = ['A', 'B', 'C', 'D']
sizes = [15, 30, 45, 10]
# 突出显示某一块
explode = (0, 0.1, 0, 0)
# 创建饼状图
plt.pie(sizes, labels=labels, explode=explode, autopct='%1.1f%%')
plt.axis('equal')  # 确保饼图是圆形的
plt.title('Pie Chart Example')
plt.legend(labels, loc='upper left')
plt.show()
```

## 五、箱线图

箱线图(Box Plot)是一种用于描述数据分布特征的数据可视化方式，它主要用于直观地展示数据的中位数、上下四分位数及异常值分布情况。

箱线图由一个长方形(箱体)和伸出的两条线(须)组成，箱体表示数据的中间50%分布区域，须则表示数据的最大值和最小值(除去异常值)。通过这种简洁高效的视觉表达，箱线图能够清楚地展示数据的集中趋势、离散程度及异常值分布情况，有助于研究者快速发现数据的整体特征。

箱线图适用于对比不同样本或条件下数据分布的差异，在统计分析、质量管理、生物医学等领域广泛应用，如比较不同地区的收入水平、不同治疗方案的疗效、不同产品的缺陷率等。

下面是一个简单示例：

```python
# 准备数据
data1 = np.random.normal(0, 1, 100)
data2 = np.random.normal(2, 1, 100)
data3 = np.random.normal(-2, 1, 100)
# 创建箱线图
plt.figure(figsize=(8, 6))
boxes = plt.boxplot([data1, data2, data3], labels=['Data 1', 'Data 2', 'Data 3'])
plt.title('Box Plot Example')
plt.xlabel('Data Group')
plt.ylabel('Value')
plt.legend([boxes["boxes"][0], boxes["caps"][0], boxes["whiskers"][0], boxes["fliers"][0], boxes["medians"][0]],
          ['Box', 'Cap', 'Whisker', 'Flier', 'Median'], loc='upper right')
plt.show()
```
