# 球场上的胜利是否等同于球场外的金钱上的胜利？

> 原文：<https://medium.com/mlearning-ai/does-winning-on-the-field-equate-to-winning-off-the-field-financially-c77817b9de0c?source=collection_archive---------2----------------------->

在此之前，我想先感谢我的导师 TJ·纳尔瓦。他帮助我探索我的求知欲，并与世界分享。谢谢你，TJ，从你的生活中抽出时间来指导一个老兵！

在这篇文章中，我想探究在球场上获胜和团队价值之间的关系。由于我已经通过创建季后赛成功的衡量标准量化了球队的成功，所以这个评估的另一半需要我收集 NFL 球队估值的信息。幸运的是，福布斯的人每年都会发布一份球队估值清单，所以找到这些信息只是在互联网上搜索的事情(对于最新的数据来说，这很容易，但随着数据变得越来越老，这是一项艰巨的任务——尽管完全值得，因为福布斯对他们的数据集收取相当高的费用)。

手头有了这些数据，我做了一个单变量回归，将季后赛成绩记录作为因变量，将球队估值作为自变量。回归分析返回的 R 平方值为 0.267052，这或多或少意味着因变量(季后赛表现)可以解释回归模型中约 26%的变化。直觉上，这是有意义的，因为单个变量无法解释像团队价值这样复杂的事情。如果有适当的信息，多变量回归适合这种类型的分析。团队价值的多变量回归模型可能如下所示:

y team Value =β共享收入(媒体权利)+β* x concessions+β* xMerchandise+β* x ticket 销售+β* x 赞助-β* x 玩家工资-β* x staff 工资-β* x stadium 租赁-β* x stadium 维护-β* x 玩家奖金

因为我试图证明一个球队的季后赛成功是计算球队价值的一个因素，所以我会将这个变量合并到模型中，如下所示:

y team Value =β共享收入(媒体权利)+β* x 娱乐点数+β* x 娱乐+β* x 门票销售+β* x 赞助-β* x 玩家工资-β* x 员工工资-β* x 媒体租赁-β* x 媒体维护-β* x 玩家奖金

对于这一分析，我将坚持使用单变量回归，因为我无法获得任何 NFL 球队的财务信息，所以我的模型看起来更像这样:

团队价值=β共享收入(媒体权利)+β* XP 裁员点

使用斜率截距值(1.397)和回归统计的系数值，我会将这些值合并到我的模型中，如下所示:

YTeam 值= 1.3897+0.081 * XP 裁员点数

将斜率截距值分配给共享收入(媒体权利)的原因是，仅一个团队的媒体权利就将使团队价值约为 13.9 亿美元(根据该模型)。鉴于赌博合法化的兴起，媒体权已经成为 NFL 的一个利润丰厚的收入来源，这反过来又与 NFL 比赛观众的增加相关。

鉴于季后赛积分系数的正值，我们可以预期球队价值会随着季后赛积分的增加而增加。随着时间的推移，我们应该会看到数据朝着这个大方向发展:

![](img/dae853dafab60c00f033a8fbb1411d6f.png)

此外，我们可以根据团队在分析的最后一年处于哪个象限来评估团队的成功:

![](img/99436a15d84f12ab9d60d62380cdf035.png)

对于这个分析，我知道我想要做一个动画数据可视化，所以我利用了 Tableau Public 中的动画特性。为了使数据可视化工作，我把两个数据表放在一起，一个是季后赛成绩，另一个是球队估价。最古老的福布斯 NFL 球队估值是从 2009 年开始的，所以我这次分析的数据范围是从 2009 年到 2020 年。凭直觉，我知道我必须通过将每个表中的“Team”列相互链接来创建表之间的关系。然而，这导致了数据可视化工作的一些问题，因为移动仅沿着一个轴而不是预期的两个轴发生。后来我发现我还需要链接“Year”列(事后看来，我可以通过创建一个数据表来简化我的工作，因为每一行中的球队价值和季后赛积分都与特定的球队和年份挂钩)。

由于我不能在 Medium 中分享 Tableau 的数据可视化动画，我截取了每一年的数据截图(你可以在这里找到我的数据，即)来说明季后赛表现和球队价值如何相对移动:

![](img/3fe5d7ac960b0464803201455917c94e.png)![](img/58d4b58fbdb35ae30506d74c6223fe5f.png)![](img/538cd0d5a66d7f9933a22273ce1c79fb.png)![](img/ad96351fde34c9ba84cf7842dcc120b9.png)![](img/7c18d2cf78a70ea2b83e3835919a41e4.png)![](img/227848acbef8ea7014ddfb9dd1035a34.png)![](img/8f8bb3e7156d0f4fc4c8950182617bf6.png)![](img/c41ea4036cbf17e38c9530f972bdcacf.png)![](img/830ec0cf78d9b24d52e4a631a96d7d69.png)![](img/d6593e5f24317d2e0025531bade38e7d.png)![](img/6e209934166e3190af9484545e3e2cef.png)![](img/77d738dd1ac2ec6eddd77b7f5acd1b8b.png)

在收集和分析数据之前，我知道在这个分析中会有两个异常值，达拉斯牛仔队和新英格兰爱国者队。尽管已经有 25 年没有赢得超级碗，但“美国队”在团队价值方面占据了至高无上的地位，不仅是最有价值的 NFL 球队，也是世界上最有价值的运动队。另一方面，新英格兰爱国者队在 2002 年至 2019 年期间赢得了六次超级碗，经历了 NFL 历史上最成功的一次比赛(这使他们与匹兹堡钢人队并列获得最多超级碗冠军)。爱国者队在这一分析中的轨迹与预期相符，即在场上获胜和场下获胜之间存在正相关。这里有一个有趣的事实:鉴于爱国者目前的估值为 44 亿美元，爱国者的所有者罗伯特·克拉夫特已经将其 1.75 亿美元的投资转化为 2400%的投资回报率。如果数据是公开的，一个真正有趣的回归分析将是评估爱国者队在罗伯特·克拉夫特拥有球队期间相对于球队成功的价值。

洛杉矶公羊队是一个有趣的观察对象。他们是一个很好的例子，说明进入一个主要的媒体市场(他们以前在密苏里州圣路易斯)可以对一个团队的估值产生几乎立即的影响。说到媒体市场，有趣的是看到有多少小的市场团队在财务和场上表现不佳。这些球队(布朗队、孟加拉队和比尔队)有什么共同点？他们处于寒冷的天气，小市场通常难以吸引自由球员。

总的来说，这是一个有趣的分析，尽管我能收集到的数据相对较少。它让我有机会利用我创建的数据集，搜索互联网以创建新的数据集，并且我学会了如何利用 Tableau 中的动画功能。

在我的下一个项目中，我将制作一个仪表板，评估萨克拉门托县合并城市的财务指标。在那之前，保重，感谢你阅读这篇文章。