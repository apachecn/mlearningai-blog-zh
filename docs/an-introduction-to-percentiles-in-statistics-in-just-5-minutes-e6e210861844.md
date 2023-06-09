# 仅用 5 分钟介绍统计学中的百分位数

> 原文：<https://medium.com/mlearning-ai/an-introduction-to-percentiles-in-statistics-in-just-5-minutes-e6e210861844?source=collection_archive---------3----------------------->

## 什么是统计学中的百分位，如何计算？

![](img/ac762d7b3d2c429714054b80cdbd3523.png)

Photo by [Karim MANJRA](https://unsplash.com/@karim_manjra?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

之前我已经写了一些关于统计数据的重要文章和一些你应该知道的重要话题

我在我的许多文章中也说过，如果你正在[学习数据科学](/@aniketkardile/how-to-start-learning-data-science-from-scratch-116e4bf61922?source=user_profile---------16-------------------------------)或者如果你正计划学习数据科学，那么统计学是你将会遇到的重要学科之一

如果你学好了这门课，相信我，你会在这个领域有很好的发展

我并不是说如果你只是学了统计学，你就能在这个领域找到工作

但是，这是数据科学领域最重要的课题之一，这就是我为什么要告诉你这些的原因

而你们很多人对统计学中的百分位数是什么，怎么算的很困惑？

所以，如果你是他们中的一员，那么不要担心，因为今天在这篇文章中，我将完全讲述这一点

这个百分比在统计学和机器学习中也非常重要

因为在机器学习中，当你建立一些预测模型时，你会遇到这种百分位数的事情

因为有一些方法可以去除数据集中的异常值

如果你不知道什么是离群值，那么不要担心，因为在下一篇文章中，我会告诉你背后的完整概念

机器学习中的人概念是一个异常值，因为当你建立预测模型时，这个概念对你来说非常重要

所以，不用浪费你太多的时间，让我们开始吧

# 什么是统计学中的百分位，如何计算？

百分位数不过是统计中使用的一种度量，表示给定数据中给定观察百分比低于的值

现在，读完这个定义，你们中的一些人可能会感到困惑，这可能会发生，因为这很难得到

所以，我会简单地告诉你，这样你会很容易理解

我想举一个例子，这样我可以很好地向你们解释，正如我在许多文章中所说的，当我们举一个例子来理解任何事情时，我们就能很好地理解它

为了向你们解释百分位数的完整概念，我将举一个分数的例子

马克= {156，165，123，135，147，148，142，139，162，168}

现在我把你可以看到的分数数据集

但是在计算百分位数或者继续之前，你需要记住一件重要的事情

那就是无论何时你必须计算给定数据集的百分位值，你都必须对数据进行排序

我在这里的意思是，因为这里我们已经举了标记的例子，我们已经为它取了数据集，所以现在我们将按升序排列我们的数据

马克斯= {123，135，139，142，147，148，156，162，165，168}

指数 1 2 3 4 5 6 7 8 9 10

正如我们在这里看到的，我们已经按升序对我们的标记数据集进行了排序

在那下面，我写下了标记数据集中每个记录的索引值

这样你就很容易完全理解这一点，而不会混淆不清

在此之前，我会告诉你给定数据集的第 50 百分位值，这样你会对这些值有一个预先的概念

值 147 = 50%百分点

索引 5

现在，您可以看到，我取了第五个索引值 147，该记录的百分位值是第 50 个百分位

现在，50%百分位的简单含义是，给定数据集中出现的全部记录中有 50%少于 147 条

这意味着 50%的学生分数低于 147 分，其余 50%的学生分数高于 147 分

现在，假设我想计算给定数据集中 90%的值，那么在索引 9 处就是 165

这仅仅意味着 90%的总值小于 165

其余 10%的值大于 165

如果你想计算第 25 个百分位的值，有一个简单的基本公式可以计算出来

为了计算第 25 个百分位数，公式为:

对于第 25 百分位，

25/100*(n+1)

其中 n 是给定数据集中元素的总数

现在，我将使用相同的示例(即 marks 数据集)来计算第 25 个百分位的值

因此，给定数据集中的元素总数是 10

所以这里我们的 n 应该是 10

n=10

现在我们将把这些值放入公式中

= 25/100*(10+1)

= 2.75

= 3

现在，在计算了第 25 个百分位数后，我们得到了 2.75 的值，但现在我们将把它向上舍入到 3

现在我们已经得到了三个值，所以给定数据集中的第三个元素是第 25 个百分位值

因此，给定数据集中的第三个元素是 139，因此我们的 marks 数据集的第 25 百分位值是 139

因此，使用这个公式，我们可以从任何给定的数据集计算出你的第 25 百分位值

如果你想计算第 50 百分位值或第 75 百分位值，你可以使用相同的公式，但在分子中，你只需要改变你的百分位值

此外，我想说的是，尝试为更多的数据集获取更多的示例，并尝试使用这种方法来计算给定数据集的百分位值

因为当你在不同的数据集上做更多的练习时，你就能很快计算出百分位值

因为现在读完这篇文章后，你可能会清楚这个概念，但几天后，你们中的一些人可能无法很快计算这些东西

所以我会说，通过举一些例子来多练习，这样你会更容易抓住这个话题

# 结论:

在本文中，我们讨论了什么是统计学中的百分位数，以及如何计算它？

因为你们很多人都混淆了百分比和百分位值

这是一个简单的方法，你可以从任何给定的数据集中找出百分位值

我希望读完这篇完整的文章后，你对统计学中的百分位有了完整的概念

而且你已经有了它背后的完整概念

所以，非常感谢你们抽出宝贵的时间来阅读这篇文章，祝你们有一个美好的未来，再见

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)