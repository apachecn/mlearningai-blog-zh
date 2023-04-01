# 蒙蒂·霍尔问题

> 原文：<https://medium.com/mlearning-ai/monty-hall-problem-e6d96ec17ed4?source=collection_archive---------4----------------------->

![](img/0886349afc992f9002b6057db6d4989e.png)

Photo by [Jeswin Thomas](https://unsplash.com/@jeswinthomas?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

“Monty Hall 问题”是一个著名的两难问题，它与游戏节目“让我们做笔交易”的参与者面临的概率有关，该节目于 1963 年在美国首次播出。在每日节目的最后，一名选手和主持人蒙蒂·霍尔一起站在三扇大门前:1 号门、2 号门和 3 号门。蒙蒂向参赛者解释说，在其中一扇门后是一个大奖，在其他的门后是一只山羊。参赛者选择其中一扇门，赢得下一扇门作为奖品。

最初获胜的机会非常明显。有两只山羊和一辆汽车。参赛者有 1/3 的机会找到赢得汽车的门，同时与蒙蒂站在门前。然而，比赛有一个诀窍:在参赛者选择一扇门后，蒙蒂打开参赛者没有选择的一扇门，并展示其中一只山羊。此时，蒙蒂会问参赛者是否想改变选择:放弃自己先选择的那扇紧闭的门，选择另一扇紧闭的门。

比如说；假设参赛者首先选择了 1 号门。让我们打开蒙蒂的 3 号门，一只山羊正在舞台上看着我们。两扇门 1 和 2 仍然关闭。如果大奖在 1 号门后面，参赛者将获胜，如果在 2 号门后面，他将失败。此时，蒙蒂会转向参赛者，询问他是否会改变主意，在 1 号门和 2 号门之间做出选择。记住，两扇门都还关着。竞争对手得到的唯一新信息是出现在他没有选择的一扇门后的山羊。

> ***他该不该改变主意？***

是的。如果竞争对手坚持自己的第一选择，有 1/3 的胜算，如果改变，有 2/3 的胜算。奇怪的是，无论竞争对手做什么，似乎都有 1/3 的胜算。有三扇紧闭的门。开始时，每个门都有 1/3 的机会颁发大奖。当他从一个门走到另一个门时，情况会怎样变化？

⭐ **答案**在于天魔堂知道每扇门后是什么。如果竞争对手选择 1 号门，后面有车；蒙蒂可以打开 2 号门或 3 号门来展示一只山羊。

🔸如果竞争对手选择 1 号门，而汽车在 2 号门后面，蒙蒂打开 3 号门。

🔸如果竞争对手选择 1 号门，而汽车在 3 号门后面，蒙蒂打开 2 号门。

🔸通过在一扇门打开后改变决定，竞争者利用了选择两扇门而不是一扇门的优势。

⭐ ***我的第二个解释*** 引出理解。假设规则略有改变。假设竞争对手像往常一样选择 1 号门、2 号门或 3 号门开始比赛。但是后来，在打开任何一扇山羊的门之前，蒙蒂说:“你愿意给你选择的门还是你没有选择的两扇门？”所以如果你选择了 1 号门。你可以离开这个门，换 2 号门和 3 号门后面的。如果你选择了门 3，你可以得到门 1 和门 2 后面的东西。事情就是这样。

这不是一个非常困难的决定。可以很清楚的看到，你应该得到两个来换取给一个门，因为这让你的胜算从 1/3 增加到 2/3。有趣的一点是:这正是在最初的游戏中，蒙蒂·霍尔在打开一扇有山羊的门后让你做的事情。这里的基本思想是:如果你必须选择两扇门，其中一扇门后面总会有一只山羊。当他在问你是否会改变主意之前打开门时:他是在帮你一个大忙！事实上，他说，“有 2/3 的机会有一辆车在你没有选择的门里，看，这不是那扇门！”如果蒙蒂打开 3 号门，把山羊带上舞台，会发生什么？你会对你的决定有不确定的感觉吗？当然不是。如果汽车在 3 号门后面，它会打开 2 号门！他没有向你透露任何事情。

⭐ ***我的第三个解释*** 是同一基本思想的更极端版本。想象一下，如果蒙蒂·霍尔给你 100 扇门的选择，而不是 3 扇门。在你选择了你的门之后，让我们假设 47 号打开了后面有一只山羊的 98 号门。现在只有两扇门是关着的。你是否应该改变主意，选择 47 号登机口，也就是你的第一选择，比如说 52 号登机口？

当然，你应该改变它。有 99%的可能性汽车在你没有选择的门后面。蒙蒂帮你打开了 98 扇你没有选择的门，他知道这些门后面都没有车。你的第一个选择有 99%的可能性是正确的。如果你的第一个选择不对，那么车就在另一扇门后，52 号。如果你想赢 100 次中的 99 次；你必须改变主意选择 52 号登机口。

🎯从中可以得出一个更广泛的教训:你对概率的直觉有时会误导你。

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)