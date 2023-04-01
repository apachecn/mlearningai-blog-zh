# XGBoost 的荣耀

> 原文：<https://medium.com/mlearning-ai/the-glory-of-xgboost-79c7369ffbad?source=collection_archive---------4----------------------->

有这么多的机器学习算法，你如何选择一个最适合你的问题？根据应用和数据，这个问题会有不同的答案。是分类，回归，有监督，无监督，自然语言处理，时间序列？有很多方法可以选择，但是在这篇文章中，我将把重点放在我特别感兴趣的算法 XGBoost 上。

# 什么是 XGBoost

XGBoost 代表 extreme gradient boosting，是一个开源库，它提供了一个高效且有效的梯度增强实现。要理解 XGBoost 是什么，我们必须先了解梯度增强。

## 群众的智慧

助推是基于群体智慧的想法，足够大的群体的意见可能比专家的意见更准确或更有力。例如，如果你在一个艺术品拍卖会上试图证明一幅画是赝品，你是愿意让 100 个艺术爱好者有 60%的机会正确预测这幅画是真的还是一个专家有 80%的机会？这是孔多塞定理的一个例子，在这个图中我们可以看到，群众的智慧占了上风。

![](img/b65bbf4c5ccdf6e18e562804c033cdfd.png)

[Source](https://royalsocietypublishing.org/doi/full/10.1098/rstb.2008.0204)

随着你的团队规模的增加，即使有足够多的人，这个机会也仅仅是随机的(50%)，这个团队的决定很可能是正确的。这就是为什么我们有一群人组成陪审团，而不是只有一个人。

## 助推

Boosting 基于群体智慧的想法，只不过群体是一群不太强大的机器学习模型，而不是人。不太强大的模型被称为“**弱学习者**”，它们的制作方式是每个模型专注于模型遇到的不同问题。该过程从根据训练数据构建模型开始，然后根据第一个模型遗漏的那些示例构建第二个模型。然后，这个过程继续建立越来越多的模型，试图填补空白，以便最终如果我们进行投票，大多数弱学习者将正确预测。这个过程可能会永远持续下去，因此需要一些停止标准，如最大模型数量或最小预测精度。

## 梯度推进

梯度推进是推进的应用，但也从梯度下降中获得灵感，梯度下降用于线性回归等机器学习算法。梯度下降的基本思想是，通过对损失函数求导，可以得到损失函数在某一点的梯度或斜率。导数的值(正的或负的)可以告诉你，为了最小化损失函数，你需要去什么方向。损失函数的斜率越大，就越接近局部最小值。

将其应用于增强的方法是，用于评估树的损失函数需要是可微分的，因此您可以计算梯度。然后，该模型将改变参数，以便进一步降低损失函数。

# 它是如何工作的

XGBoost 只是渐变增强的一个调整版本，因此它在功能上以相同的方式工作。人们使用 XGBoost 而不是普通梯度提升的区别和原因是它的执行速度和模型性能。对梯度增强进行了许多优化，但主要变化如下:

梯度增强仅计算一阶梯度，这意味着它将对损失函数进行求导，不再进一步。XGBoost 将计算损失函数的二阶，以获得更多关于模型应如何变化的信息，从而获得更好的结果。获得的信息特别是关于损失函数如何表现以及参数变化将如何影响损失函数。

另一个主要变化是使用了高级正则化 XGBoost，以便更好地进行泛化。正则化通过不让模型学习数据中的噪声来帮助模型不过度拟合。如果模型只能学习数据中最重要的方面，它就不会被数据中更细微的变化绊倒，而是能够看到“更大的图景”

# 什么应用是最好的

XGBoost 是一个令人惊讶的算法，可以用于回归和分类。下面是我使用 XGBoost 对美国职业棒球大联盟比赛结果进行分类的一段代码。

# 结论

有许多不同的机器学习算法，每种算法都有许多不同的变体，那么如何选择最好的算法呢？既然机器学习正在成为一个如此庞大的行业，那么关于什么模型可以在什么样的问题上表现得最好，一直都有新的发现。找到最佳算法的方法是不断更新已经开发的新算法或算法版本，并尝试它们。您可以做一定程度的规划来选择适合您的数据的算法，但您永远不会知道，直到您尝试。