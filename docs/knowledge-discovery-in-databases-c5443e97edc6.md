# 数据库中的知识发现

> 原文：<https://medium.com/mlearning-ai/knowledge-discovery-in-databases-c5443e97edc6?source=collection_archive---------10----------------------->

数据科学是通过识别数据中的模式从数据中提取知识的科学。数据库中的知识发现(KDD)是识别数据模式的方法之一，换句话说，它是理解数据的过程。

在医药、天文、金融、零售、营销等各个领域。数据库有了巨大的增长，手动分析和解释数据是不可能的。需要使用具有高计算能力的现代技术来分析这些数据。此外，用户的期望与日俱增，例如，在线商店的要求是根据不同的类别显示其商店中所有可用的产品，今天在线商店的主要要求是向正确的顾客推荐正确的产品。

KDD 解决了数据过载的问题，它试图通过提供一种合适的方法来从这些巨大的数据库中发现知识，从而为这个问题提供解决方案。*数据挖掘*是 KDD 的一个步骤，处理应用算法从数据中提取模式。

# KDD 路线图

法耶兹等人(1996)将数据库中的知识发现(KDD)定义为在数据中识别以前未被识别或发现的正确的、可解释的和有用的模式的重要过程。

由于 KDD 是一个过程，它涉及各种步骤。KDD 进程是迭代的，也是互动的。以下是在 KDD 需要遵循的步骤

1.  **问题规范** —在这一步中，收集了关于问题领域的更多信息。对应用领域的理解是为了建立整个过程的目标。
2.  **资源收集** —这一步，收集所需的软件、硬件、数据等所有资源。根据需要从数据库中选择数据库的子集。
3.  **数据清理** —这一步的输出是一个清理后的操作数据库。该步骤包括几个清理操作，例如处理数据中的缺失值、处理异常值、根据目标字段平衡数据库等。
4.  **数据预处理** -在此阶段，在特征级别对数据进行更改，如使用数据库中的原始特征创建新特征(列)，删除特征等。
5.  **数据挖掘任务的选择** —有分类、聚类、回归、关联等多种数据挖掘任务。根据 KDD 进程的目标，任务被映射到数据库。
6.  **模型选择** —在这一步，选择数据挖掘算法和提取模式的方法。此外，为了获得 KDD 的最佳结果，要选择用于数据挖掘算法的参数。
7.  **数据挖掘** —在这一步中，通过使用所选择的数据挖掘任务和算法来提取模式。此外，在该步骤中评估模型，使用各种评估标准测试算法的性能。
8.  **解释** —提取的模式然后使用几种可视化技术进行解释。此外，在这个阶段，可以根据数据挖掘步骤之后建立的模型来可视化数据。
9.  **根据知识采取行动** —在这一阶段，根据使用上述所有步骤获取的知识采取行动。这些步骤还澄清了之前关于问题或应用程序域的冲突。

所有上述步骤都是高度迭代的，KDD 过程的任何两个步骤之间都可能存在循环。

参考文献-

[1] Vijay Kotu 和 Bala Deshpande，2019，《数据科学》(第二版)，摩根·考夫曼，[https://doi.org/10.1016/B978-0-12-814761-0.00001-0](https://doi.org/10.1016/B978-0-12-814761-0.00001-0)。
([https://www . science direct . com/science/article/pii/b 9780128147610000010](https://www.sciencedirect.com/science/article/pii/B9780128147610000010))

[2]法耶兹，u .，皮亚泰茨基-夏皮罗，g .和史密斯，p .，1996 年。从数据挖掘到数据库中的知识发现。*艾杂志*， *17* (3)，第 37–37 页。

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)