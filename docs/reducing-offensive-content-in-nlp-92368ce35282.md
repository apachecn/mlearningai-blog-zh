# 减少自然语言处理中的不良内容

> 原文：<https://medium.com/mlearning-ai/reducing-offensive-content-in-nlp-92368ce35282?source=collection_archive---------3----------------------->

## NLP 模型，如 GPT-3 或地鼠，有时会产生令人不快的内容。这限制了它们在现实生活中的使用。Red Teaming (RT)减少了 NLP 模型的有害输出，而无需昂贵的人工注释。

![](img/a0908f265cc9567201b41a394e0945c8.png)

Photo by [Nick Fewings](https://unsplash.com/@jannerboy62?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

NLP 模型旨在与真实的人互动。GPT-3 和地鼠是最先进的自然语言处理模型。然而，它们有时都会产生有害的内容。

在现实生活中，这种有偏见的模型是有风险的。一个坏演员可以使用这些 NLP 系统来产生有毒的语音。

有害内容可能从有毒言论或政治观点到分享个人信息或刻板印象。

有多种选择可以降低这些风险。我们将首先讨论人在回路中的方法。然后，我们将讨论红色团队方法。

**回路中的人类**

从 NLP 模型中获得人类反馈是有好处的。人们不喜欢依赖黑盒算法。

然而理解 NLP 模型是复杂的。Gopher 模型吸收 10.5 TB 的文本。没有人能够检查如此大的数据集。我们既不能理解它的 2800 亿个模型参数。然而，我们能够审查它的输出是否令人不快。

人工注释是有用的。我们可以用它来检测有害的输出。我们可以雇人来检查 NLP 模型的输出。如果他们检测到有害输出，我们可以将其排除。

然而雇佣人来做这项工作是很昂贵的。OpenAI 要求用户提供关于 NLP 输出的反馈。除了人类注释者之外，OpenAI 还雇佣了其他人来审查模型输出。这样就打开了人工注释的自动化部分。

这种方法的缺点仍然是可伸缩性差。该方法仅检查少量可能的 NLP 模型输出。

然而，有害的定义可能会随着时间的推移而改变。因此，我们更喜欢一种方法，我们可以随着时间的推移进行升级，并将其扩展到更大的数据集。

分类算法优于人工注释。我们可以向分类器提供无限量的 NLP 输出。我们将能够选择更多的进攻输出。它将进一步改进分类器。这增加了检测到的攻击性输出的数量。

因此，我们将识别新的攻击性内容类别。让我们详细回顾一下这样的系统。

**红队**

Red Teaming (RT)是一种修复 NLP 模型等系统的对抗方法。基本思想是用 NLP 模型创建恶意输出。然后，我们排除这些恶意输出。

让我们一步步回顾这个过程。

我们首先创建一个 rt 分类器来检测有害的输出。创建分类器有多种方式。我们可能有明确定义的数据集，其中的类别已经分为攻击性和非攻击性内容。然而，最理想的是，分类器将学会自己分离这些类别。

接下来的步骤是使用我们的 NLP 模型生成输出。例如，我们使用 GPT-3 或地鼠模型生成文本。

RT 分类器将这些输出分类为有害和无害。

如果我们检测到攻击性输出，我们可以使用两种方法将其排除。我们可以在没有这些有害例子的情况下训练我们的 NLP 模型。这样，NLP 模型将不包括这样的数据。我们可以选择将此类攻击性内容添加到模型黑名单中。这样，在生成输出时，我们将不会使用它们。

RT 并不意味着取代人类的判断。然而，该方法是在人类反馈之前发现有害内容的预防性方法。这在帮助使 NLP 模型更难以以错误的方式使用方面特别有用。

最后更新 2022 年 3 月

来源:

[**佩雷兹等人 2022 年 2 月**](https://arxiv.org/pdf/2202.03286.pdf)

[**欧阳等人 2022 年 1 月。**](https://cdn.openai.com/papers/Training_language_models_to_follow_instructions_with_human_feedback.pdf)

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)