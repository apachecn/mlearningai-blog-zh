# 图形模型上的推理—第一部分

> 原文：<https://medium.com/mlearning-ai/inference-on-graphical-models-part-1-ae3f6bc1d7f6?source=collection_archive---------5----------------------->

在本文中，我们将开始一系列关于图形模型的推理。在本系列中，我们将看到网络的结构，即条件独立性断言和联合分布的相关因子分解，对于我们甚至能够执行推理的能力是重要的。我们将主要关注条件概率查询，即具有以下形式的查询:P(Y | X= x)。在本文中，我们将从简单分析*精确推理*和*近似推理*的复杂性开始。