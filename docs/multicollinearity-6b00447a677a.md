# 多重共线性

> 原文：<https://medium.com/mlearning-ai/multicollinearity-6b00447a677a?source=collection_archive---------1----------------------->

## [机器学习](https://machine-learns.herokuapp.com/)

## **什么**、**为什么、**和**如何解决**多重共线性。

![](img/543257e39de53f7f89c862785fe743fd.png)

Image by [Analytics Vidhya](https://www.analyticsvidhya.com/)

你知道多重共线性对机器学习模型的**最终精度**几乎没有影响**吗？**那么为什么多重共线性是一个问题**，它首先是什么？**

在这篇文章中，我们将学习这些问题的答案。

# 描述—

*   回归模型中的假设。
*   什么是 Coliniarity？
*   关于多重共线。
*   为什么多重共线是一个问题？
*   如何去除多重共线性？

> 1.**使用 VIF** 及其代码实现
> 
> 2.**使用相关性**及其代码实现
> 
> 3.一个自动化上述方法的 **python 库**。

# 假设—

非常重要的是要知道基于回归的模型的一个假设是—

*   **没有或几乎没有多重共线性，即**输入要素彼此之间**没有相关性**，或者换句话说，它们彼此**独立**。

但通常情况并非如此，即数据集包含彼此显著相关的要素。这导致多重共线性。

让我们简单地看一下什么是 Coliniarity。

# 什么是共线性？

**共线性**或**相关性**是一种统计度量，表示两个或多个变量一起移动的程度。换句话说，**它只是一个数字(+ve 或-ve)来表示两个特征如何相互作用，就像如果一个特征增加，另一个特征增加、减少或显示随机增长。**

**相关性可以是正的，也可以是负的。**正相关表示变量一起增加或减少。负相关表示如果一个变量增加，另一个变量减少，反之亦然。

# 关于多元共线—

众所周知，了解影响商业公司增长的因素非常重要，这可以通过多种方式完成，其中一种方式是了解我们的机器学习模型给出的方程。让我们举个例子-

**covied 19**的数量**= 4 *面积+截距**(只是一个假设)

假设我们的模型给出了上述等式，该等式基本上说明了如果截距为 0，那么我们可以直接说，如果面积加倍，covid 案例的数量将增加 4 的**倍。你可以理解，尽可能准确地了解这个因素**是非常重要的**，因为基于此，我们应该决定每天生产的疫苗和病床数量。******

# **为什么多重共线是一个问题？**

**那么多重共线性和上面的例子有什么关系呢？**

****由于多重共线性**，我们可能会获得相同因素的不同**系数**，从而导致**错误解释**，这可能会产生严重影响。例如，我们可能得到一个因子为**2 *面积**，但这将导致每日生产的**床位**和**疫苗**数量**短缺**，因此将导致每日死亡人数**增加。****

## **总的来说，我们可以说—**

> ****多重共线性对这些系数有很大的负面影响，并可能导致错误的推断。****
> 
> ****从技术上讲，它也会影响 p 值，而 p 值又会影响特征选择过程。****

# **如何去除多重共线性？**

**一般来说，有两种不同的方法可以消除多重共线性—**

> **1.使用相关性**
> 
> **2.使用 VIF(变动通货膨胀系数)**

## **1.使用相关性**

**通常，两个特征之间的相关性大于 0.7，这表明那些特征**

**两个特征之间的相关性大于 0.7 表明存在多重共线性，我们应该丢弃两个特征中的一个来解决它。**

## **代码—**

**[Github Gist on Multicoliniarity(Correlation)](https://gist.github.com/Sudhanshu1304/ef10339c6f78a65e3015493f053585a0)**

## **2.**变动通货膨胀系数(VIF)——****

**有一个识别多重共线性的简单测试叫做 **VIF** (方差膨胀因子)。 **VIF** 从 1 开始，没有上限。1 到 5 之间的 VIF 被认为是适中的，但是如果 VIF 超过 5，那么这些将被删除。**

```
**VIF = 1/(1-R2)**
```

**R2 是一个决定系数，它表明了一个预测因子能够解释响应变量变化的程度。**

****VIF 为 10 意味着如果没有共线性，则预测值系数的方差比应有值大 10 倍。****

## **代码—**

**[Github Gist on Multicoliniarity(VIF)](https://gist.github.com/Sudhanshu1304/e880c22aadbfb3ef23b7c2dfe174d011)**

## **图书馆支持—**

**您可以使用 Python 库 **ModelAuto 来**轻松解决多列性。**

**它有一个内置的包，可以通过这两种方法消除多重共线性。**

```
**pip install ModelAuto****from ModelAuto.Multicollinearity import handel_Multico_Corr**OR**from ModelAuto.Multicollinearity import handel_Multico_VIF**
```

# **结论—**

> **多重共线性会影响系数和 p 值，**，但不会影响预测、预测精度和拟合优度。因此，如果我们的主要目标只是进行预测，我们就不需要减少多重共线性。****
> 
> ****多重共线性主要影响线性模型，如线性回归、物流回归。对 KNN、决策树等非线性算法没有太大影响。****

**如果你觉得这些信息有帮助，可以考虑留下👏😏。**