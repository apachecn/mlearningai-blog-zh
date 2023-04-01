# 监督机器学习中(坏)数据质量对模型准确性的影响——来自模拟研究的结果

> 原文：<https://medium.com/mlearning-ai/the-effect-of-bad-data-quality-on-model-accuracy-in-supervised-machine-learning-results-from-117d150df755?source=collection_archive---------4----------------------->

数据质量显然对数据科学和接收结果的有效性起着重要作用。本文讨论了数据质量不能追溯改进的情况，您需要对这些数据进行分析。

与没有数据质量问题的数据集相比，监督机器学习的模拟研究已用于量化(差的)数据质量对结果准确性的影响。

在这些模拟案例研究中，研究了以下 4 个[数据质量标准](https://gerhard-svolba.medium.com/is-your-data-ready-for-data-science-motivating-this-topic-from-a-sail-race-analysis-example-7dde97a68e4d)

*   **数据量——我需要多少数据？**根据模型结果研究不同数量的可用观察和事件。
*   **数据可用性** —在这些案例研究中分析了保留最重要变量集的后果。
*   **数据正确性—“数据中的偏差”** —如果在监督机器学习中引入输入和目标变量中的随机和系统偏差，会发生什么
*   **数据完整性**:缺失值如何影响预测能力？

本文详细讨论了前三个标准的模拟结果。“数据完整性/缺失值”的详细信息在另一篇文章中说明:[量化监督机器学习模型中缺失值对模型准确性的影响](https://gerhard-svolba.medium.com/quantifying-the-effect-of-missing-values-on-model-accuracy-in-supervised-machine-learning-models-8d47d7eca921)

# 结论

从模拟研究中可以得出以下结论:

## 增加事件和非事件的数量很重要

仿真结果表明，随着事件数和非事件数的增加，模型质量提高。对于多达 250 个事件的情况尤其如此，但对于事件更多的情况也是如此。额外的数据仍然在一定程度上提高了模型质量。

## 年龄变量是重要的，变量之间存在补偿效应

在所有的模拟数据集中，都存在一个年龄变量。从可用输入变量列表中删除年龄变量显示变量质量下降。然而，也已经表明，在最佳模型中输入变量的不可用性可以在某种程度上由其他输入变量来补偿。

## 数据干扰是仅出现在训练数据中还是同时出现在训练和评分数据中是有区别的

模拟已经表明，是只有训练数据因缺失或不正确的数据而有偏差，还是训练和评分数据都有偏差，这是有区别的。偏向评分数据会降低模型质量。

## 随机扰动对模型质量的影响远小于系统扰动

已经表明，许多模型可以在一定程度上处理随机干扰。然而，系统偏差的引入会导致模型质量的大幅下降。

# 通用模拟程序

## 预处理

对于模拟，使用了具有二元目标变量的监督机器学习任务。这些数据来自不同行业的四个真实数据集。

为了有一个用于模拟的“完美的”起始数据集，数据已经以下列方式进行了预处理。这导致了没有缺失值的训练数据集。

*   如果一个变量有超过 5 %的缺失值→该变量被删除
*   剩余变量的缺失值的观测值(≤ 5%的缺失值)将从分析中移除。

运行多个建模周期以检索具有良好预测能力的稳定模型。该变量的变量列表被冻结，以便在模拟中使用。

## 运行模拟

下图显示了模拟及其评估的程序。数据被分成训练和验证数据。测试分区被用作“评分数据”,以反映模型训练中未使用的数据集。这允许评估模型评分中缺失值的影响。

![](img/a3b320f07090a1735acc628269f2715d.png)

在下一步(蓝色矩形)中，执行数据的“特定场景”预处理。这包括例如

*   为分析数据量而删除记录
*   输入变量的去除
*   向数据中引入偏差
*   缺失值的插入

最后，基于该数据训练具有冻结变量集的回归模型，并评估结果。

**模拟场景中模型的可能偏差**

注意，在不同的模拟场景中为预测模型提供一组预定义的最佳变量会产生对过于乐观的模型性能的偏向。该模型不需要找到预测变量的最佳集合。对于存在数据质量问题的数据，例如观测值不足、大量缺失值、输入数据中的偏差以及最佳预测变量的选择可能不会产生最佳数据集。

数据质量会影响最佳输入的选择。因此，模拟场景受到这种先验变量选择的影响(并且因此受到先验知识的影响)。尽管如此，我们还是决定提供一组预定义的变量，以便进行比较，并消除变量选择差异可能导致的情景结果偏差。

# 业务案例计算的框架

## 介绍

一个虚构的参考公司用于根据不同模拟场景的结果计算业务案例。模型质量的变化被转换为响应率，相应的利润以美元表示。

这样做是为了从业务角度说明不同数据质量变化的影响。需要注意的是，以美元表示的数字仅应被视为基于模拟情景假设和此处所述商业案例的粗略指标。在个别情况下，这些价值和关系有些不同。

## 参考公司质量数据通信

以下章节中的参考公司 Quality DataCom 在通信行业开展业务。该公司拥有 200 万客户，并开展活动来促进其产品和服务的交叉销售和追加销售。在一个典型的活动中，通常会联系大约 100，000 个响应概率最高的客户(客户群的 5%)。客户对报价(接受报价或产品升级报价)的平均反应代表 25 美元的利润。

假设您使用的分析模型正确预测了前 5%客户群中 19%的肯定回答。这里的“响应”是指营销活动联系人导致产品购买或升级。此次活动总共吸引了 19，000 名响应客户，创造了 475，000 美元的利润(19，000 x 25 美元)。

# **数据量—我需要多少数据**

对于模拟，数据量的变化以两种不同的方式进行:

**事件数量的变化(蓝线)**

在这里，事件逐渐从数据中删除，以便研究如果较少的事件可用于建模，预测能力的变化。非事件不会从数据中删除。

这反映了经常遇到的情况，即数据中有足够数量的非事件，但只观察到有限数量的事件。

仅事件数量的变化，而保持非事件数量不变，隐含地导致事件和非事件之间的采样比的变化。然而，这不是这里进行的研究的重点。

**一般观测值的变化数(红线)**

为了研究对预测能力的影响，这里系统地减少了观察值的数量。事件和非事件都从数据中删除，因此事件和非事件之间的采样比率保持(近似)恒定。

这反映了可用于分析的观测值数量有限的情况。此场景说明了额外观察对预测能力的影响(例如，通过提供更多客户记录或采访更多受访者)。

## 结果

![](img/90b3615d503608862563be25b7bc0648.png)

Comparison of the %Response between “only events excluded” and “events and
non-events excluded

正如所料，响应百分比随着事件数量的增加而增加(蓝线)。在 50 到 100 个观察值的范围内，可用事件案例的增加与模型性能的提高之间有着密切的关系。超过 400 个事件后，改进会变小。1000 以上(2000 和 5000)，只能看到车型质量略有提升。

这些结果隐含地显示了两种情况之间的差异，在这两种情况下，要么仅从数据中删除事件，要么从数据中删除事件和非事件。如果只从数据中删除事件，模型质量会更好，因为非事件仍然为模型提供信息。

对于多达 1，000 个事件的场景，是只从数据中删除事件还是同时删除事件和非事件会有所不同。因此，一旦总样本量不够大，数据中的额外非事件记录也有助于模型的预测能力，因为这增加了总“n”

## 计算业务案例

对于上述参考公司，这些结果意味着:

*   运行已经在 50 个事件上训练的活动具有 268，500 美元的预期累积利润，而训练数据中的 100 个事件具有 364，000 美元的预期累积利润。
*   因此，如果训练数据包含 100 个事件而不是 50 个事件，则每个活动可以产生 77，500 美元的额外利润。这是训练数据中每个额外事件的 1，550 美元的额外利润。
*   在更高的基础上增加活动总数(例如，从 500 增加到 1，000)仍然可以为每个活动带来 13，750 美元的额外总利润。细分为培训数据中每个额外事件的额外利润，结果是$27.50。
*   运行已经在 50 个事件上训练的活动具有$372，750 的预期累积利润，而训练数据中的 100 个事件具有$418，750 的预期累积利润。
*   如果训练数据包含 100 个事件而不是 50 个事件，这导致每个活动的额外利润为 46，000 美元。这是训练数据中每个额外事件的 920 美元的额外利润。
*   在事件数量较高的情况下(例如，500 和 750)，每个活动的额外利润仍为 18，500 美元。并且训练数据中每个额外事件的额外利润仍然是 74 美元。

# **数据可用性** —如果我不能使用某些变量怎么办？

在这些案例研究中，分析了保留最重要的变量集的后果。

本节描述的分析基于变量的可用性。如果某个子集允许您建立一个好的模型，那么研究如果从训练数据中删除这组变量，该模型的预测能力会降低多少。在这种情况下，分析模型必须使用其他变量进行建模。

变量之间的相关性在某种程度上对于确定缺失值和替代预测变量的代表性替代值是重要的。例如，如果某个变量被认为对模型很重要，但却不可用，则其他变量可能会接管其预测内容和能力，因为它们是相关的。

已经研究了以下场景:

*   可以使用除客户年龄变量之外的所有可用变量的无约束模型**(没有年龄的模型 1)。请注意，这里特意选择了客户年龄，因为在许多情况下，这是一个非常重要的变量(第 16 章中介绍的所有四个基线模型都使用客户年龄变量)，但它通常无法提供，或者只能在(系统)缺失值的情况下提供。**
*   可以使用所有可用变量**的无约束模型，除了年龄变量和与年龄**在同一变量群中的那些变量(没有年龄群的模型 1)。这种情况反映了这样一种情况，即某个变量的不可用性经常触发相关变量的不可用性。如果不同的变量是从事务性数据中的同一变量派生出来的，情况尤其如此。如果此变量不可用，基于它的所有派生变量也将不可用。
*   可以使用所有变量的模型，除了无约束模型中的变量(模型 2[无模型 1 变量])。
*   可以使用所有变量的模型，除了模型 1 和 2 中的变量(模型 3[没有模型 1 和 2 变量])。
*   可以使用除模型 1、2 和 3 中的变量之外的所有变量的模型(模型 4[没有模型 1、2 和 3 变量])。

## 结果

![](img/ce4b823a982ff89658f38d527b21582b.png)

对于模拟数据，结果显示从模型 1 到模型 4 的可用性的平均响应百分比单调下降。

有趣的是，移除年龄变量导致平均%响应从 16.4%下降到 14%，这几乎与从模型 1 到模型 2 的下降一样强烈。这意味着当排除模型 1 变量时，年龄变量的不可利用性单独解释了几乎所有%反应的减少。

您还可以看到，没有年龄组变量的模型 1 低于模型 2%的响应。这意味着即使去除了年龄变量，模型 2 也表现得更好，因为该模型可以包括年龄的相关替代变量，这在去除了与年龄相关的变量的模型中是不可用的。

## 商业案例的结果

> 对于上述参考公司，去除年龄变量的结果意味着有年龄变量的预期累积利润为 410，000 美元，没有年龄变量的预期累积利润为 350，000 美元。60，000 美元的绝对差额可能会引发对客户数据库中年龄变量的完整性和正确性的特别关注。

# **数据正确性—“数据中的偏差”**

## “看不见的”数据质量问题

在许多情况下，数据正确性是一个看不见的数据质量问题，因为它经常不能被明确地看到。与缺失值不同，缺失值可以从数据中显式查询并针对每个变量进行汇总，可用数据是否有偏差不能仅通过检查值来检测。这里通常应用业务和验证规则来决定一个值是否正确。

根据数据正确性，有[不同的方法](https://www.youtube.com/playlist?list=PLdMxv2SumIKsqedLBq0t_a2_6d7jZ6Akq)来描述数据质量状态。在某些情况下，基于值范围、值列表或完整性检查的硬事实规则可用于检查值是否正确。然而，在其他情况下，检查数据正确性的结果只能在概率的基础上完成(比如“值可能不正确”)。例如，统计方法可用于标记超出基于标准差计算的验证上限和下限的观察值。

## 随机和系统偏差

作为一名数据科学家，你应该区分数据中的随机偏差和系统偏差。不管其他变量如何，每个分析对象都以相同的概率出现随机偏差。此外，偏见本身并不系统地指向一个方向。

假设每个分析对象以不同的概率出现系统性遗漏偏差。偏置的方向也可以是系统地向上、向下或朝向中心。例如，考虑所有观察值显示相同值或所有具有大值的观察值显示小值的情况。

为简单起见，通过定义 10 个大小相等的分析对象集群，在数据中创建了系统偏差值。具体到相应模拟场景的定义，一个或多个集群中所有观测值的变量是有偏差的。

## 评分数据分区中有偏差的值

为评估输入变量中偏差的影响而执行的模拟是这样设置的，即用于评估模型质量的数据分区也具有偏差值。

这种情况指的是数据质量问题(如有偏差的值)不仅发生在模型训练阶段，还发生在模型应用中。这种情况指的是数据质量问题尚未修复，并且存在于训练和评分数据中的情况。

## 场景概述

基于这些数据创建了以下场景

*   R0:数据中没有引入偏差。
*   R0.5:从标准化区间输入变量中随机添加/减去半个标准差。
*   R1:从标准化的区间输入变量中随机增加/减去一个标准差。
*   R2:从标准化的区间输入变量中随机增加/减去两个标准差。
*   R3:从标准化区间输入变量中随机添加/减去三个标准差。
*   S0:输入变量的值被设置为 0。
*   S-1:输入变量的符号改变。

## 结果

![](img/9c39183f9c500e88ecc4301070b7a70d.png)

Box plot for %Response for different settings of random and systematic bias in the training
and scoring data

可以看到，输入数据中随机扰动量的增加降低了平均响应率，从 R0 的 19.29 降至 R1 的 17.63、R2 的 15.88 和 R3 的 14.99。这意味着与 R0 相比，R1 的应答率(+/- 1 标准偏差)的相对损失已经是 8.6 %。

你还可以看到，系统性偏差的影响要大得多。情景 S0 降至 15.55 %，情景 S-1 降至 13.63 %。

# 模拟研究的结论

从数据质量的角度来看，可以从模拟研究中得出以下结论

## 增加事件和非事件的数量很重要

仿真结果表明，随着事件数和非事件数的增加，模型质量提高。对于多达 250 个事件的情况尤其如此，但对于事件更多的情况也是如此。额外的数据仍然在一定程度上提高了模型质量。

## 年龄变量是重要的，变量之间存在补偿效应

在所有的模拟数据集中，都存在一个年龄变量。从可用输入变量列表中删除年龄变量显示变量质量下降。然而，也已经表明，在最佳模型中输入变量的不可用性可以在某种程度上由其他输入变量来补偿。

## 数据干扰是仅出现在训练数据中还是同时出现在训练和评分数据中是有区别的

模拟已经表明，是只有训练数据因缺失或不正确的数据而有偏差，还是训练和评分数据都有偏差，这是有区别的。偏向评分数据会降低模型质量。

## 随机扰动对模型质量的影响远小于系统扰动

已经表明，许多模型可以在一定程度上处理随机干扰。然而，系统偏差的引入会导致模型质量的大幅下降。

# 网络研讨会演示

# 链接

上文显示了两个相关分析网络研讨会的链接。我的 [**数据科学的数据准备**](https://www.youtube.com/playlist?list=PLdMxv2SumIKsqedLBq0t_a2_6d7jZ6Akq) 网络研讨会包含更多关于该主题的内容。

中型文章:[您的数据为数据科学做好准备了吗？——从一个帆船比赛分析的例子引出这个话题](https://gerhard-svolba.medium.com/is-your-data-ready-for-data-science-motivating-this-topic-from-a-sail-race-analysis-example-7dde97a68e4d)

中篇:[https://Gerhard-svo LBA . medium . com/is-your-data-ready-for-data-science-motivating-this-topic-from-a-sail-race-analysis-example-7 DDE 97 a 68 e 4d？](https://gerhard-svolba.medium.com/is-your-data-ready-for-data-science-motivating-this-topic-from-a-sail-race-analysis-example-7dde97a68e4d)

medium Article:[https://Gerhard-svo LBA . medium . com/quantitating-the-effect-of-missing-values-on-model-accuracy-in-supervised-machine-learning-models-8d 47d 7 ECA 921](https://gerhard-svolba.medium.com/quantifying-the-effect-of-missing-values-on-model-accuracy-in-supervised-machine-learning-models-8d47d7eca921)

[https://www.youtube.com/watch?v=61mKcvEj5a0&list = pldmx v2 sumiksqedlbq 0t _ a2 _ 6d 7 JZ 6 akq&index = 8](https://www.youtube.com/watch?v=61mKcvEj5a0&list=PLdMxv2SumIKsqedLBq0t_a2_6d7jZ6Akq&index=8)

SAS 社区文章:[使用 SAS Enterprise Miner 进行预测建模模拟研究](https://communities.sas.com/t5/SAS-Communities-Library/Using-SAS-Enterprise-Miner-for-Predictive-Modeling-Simulation/ta-p/641560)

我的幻灯片收藏[中的第 102 号演示文稿](https://github.com/gerhard1050/DataScience-Presentations-By-Gerhard)包含更多关于这个主题的视觉效果。

![](img/03b2b9233ab2bad558d66127e9f3cad5.png)

我的 SAS 出版社书籍“[使用 SAS 进行分析的数据质量](https://github.com/gerhard1050/Data-Quality-for-Data-Science-Using-SAS#readme)”中的第 16、17、18 和 19 章更详细地讨论了这些主题。

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)