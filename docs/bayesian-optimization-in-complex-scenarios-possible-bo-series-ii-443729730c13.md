# 复杂场景下的贝叶斯优化:可能！(博系列二)

> 原文：<https://medium.com/mlearning-ai/bayesian-optimization-in-complex-scenarios-possible-bo-series-ii-443729730c13?source=collection_archive---------0----------------------->

![](img/ecfa7e2e14b69f4e1d5847111f4b3162.png)

如果你读过我关于贝叶斯优化的第一篇文章，你会发现它可以用来获得全局黑盒函数 f( **x** )的最大值或最小值的近似值。然而，这并不是贝叶斯优化的唯一用途！不要忘记贝叶斯优化不仅仅是一种算法，而是一类可以用来解决复杂场景的方法，比如我在本文中介绍的那些。特别是，这篇文章很大程度上是基于我的论文[1]的工作，所以如果你想知道更多的细节，请随时阅读它，并给我发电子邮件与疑虑或想法。

这里有一些你可以应用经典贝叶斯优化算法的修改版本的场景:

*   **有几个约束的多目标优化问题:**这显然包括我们想要优化几个黑盒或者仅仅一个黑盒的问题，这些黑盒受制于几个约束的存在。特别是，存在涉及同时优化几个黑盒的问题。在大多数情况下，这些黑盒是反向相关的。例如，考虑机器学习算法的超参数调整问题。这里，我们想要同时优化神经网络的泛化误差的估计和预测时间。因此，有一个权衡，最小化神经网络预测时间的解决方案不期望提供低的泛化误差估计，反之亦然。因此，解决方案是超参数的一组配置，这些配置显示了所有目标的最佳权衡，称为 Pareto 集，可以使用新的采集函数找到该集[2]。
*   **在贝叶斯优化中包含整数值和分类变量:**贝叶斯优化，正如我们所见，只对真实变量有效。然而，诸如 ML 算法的超参数调整的问题包括整数值和分类变量的函数的优化。例如，深度神经网络的超参数除了学习速率之外，还可以包括层的数量，这是一个整数值变量，以及激活函数，这是一个分类变量。问题在于，贝叶斯优化通常使用高斯过程作为概率代理模型，以在每次迭代中构建获取函数。此外，高斯过程的大多数内核(我将在另一篇文章中解释的模型)以及具体用于 BO 的那些内核，都假设了实值变量。解决方案是创建一个转换，允许一个有效的 GP 内核处理整数和分类值变量[3]。
*   **并行评估的贝叶斯优化:**标准贝叶斯优化算法每次只允许评估一个可能的配置。然而，在大多数情况下，这是低效的，例如，如果您有一个计算集群，其中我们能够同时评估几个点，这将浪费资源。因此，希望设计一种允许贝叶斯优化在每次迭代中提供一组点来评估目标的过程。
    我的论文提出了一种信息论方法的扩展，用于在受限的多目标场景中进行并行评估【4】。有一个类似的设置叫做**非近视贝叶斯优化**，我们不是在一个单一的步骤中优化函数，而是在 n 次迭代中找到问题的最优答案，这就是最优解集。这种方法效率更高，但是计算量非常大。
*   **异步贝叶斯优化:**如我们所见，贝叶斯优化可以同时建议多个点。但是，当我们评估神经网络的几种配置时，有时某些设置比其他设置评估起来更便宜。例如，训练一个只有 2 个隐藏层的深度神经网络比训练一个有 100 个隐藏层的网络要便宜。完美的设置是能够一直评估配置，而不必等待批处理的所有配置完成。然而，这个想法在一个受约束的多目标场景中很难实现，但是你可以等待。

而且还有更多的设定！像**考虑复杂变量**而不是结构化数据。例如，相对于所有可能的照片优化一张照片。在这些设置中，我们需要提供一个高斯过程或可行变换的特定核心。我们也可能解决位于单纯形而不是超立方体(对金融有用)中的问题。如果你想了解更多，请订阅，不要忘记尽可能在工作中享受乐趣！

[1]加里多·默汉，欧洲委员会(2021 年)。复杂情况下贝叶斯优化的高级方法。

[2]加里多-默汉和埃尔南德斯-洛巴托(2019 年)。约束多目标贝叶斯优化的预测熵搜索。*神经计算*， *361* ，50–68。

[3]加里多-默汉和埃尔南德斯-洛巴托出版社(2020 年)。用高斯过程处理贝叶斯优化中的分类变量和整数值变量。*神经计算*， *380* ，20–35。

[4]加里多-默汉和埃尔南德斯-洛巴托出版社(2020 年)。约束多目标贝叶斯优化的并行预测熵搜索。arXiv 预印本 arXiv:2004.00601

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)