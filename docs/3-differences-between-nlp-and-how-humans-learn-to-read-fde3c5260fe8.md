# 自然语言处理和人类学习阅读的 3 个不同点

> 原文：<https://medium.com/mlearning-ai/3-differences-between-nlp-and-how-humans-learn-to-read-fde3c5260fe8?source=collection_archive---------7----------------------->

人类语言学习和自然语言处理(NLP)几乎完全不同。尽管 NLP 中最近的创新具有强大的能力，但这些方法仍然无法实现真正的自然语言理解。最终，*理解自然语言比熟练处理任务要困难得多。人类学习和 NLP 之间的差异似乎是显而易见的，但值得探究人类学习和 NLP 之间最重要的差异，以阐明为什么当前的方法中存在这些缺陷。*

1.  **数据格式**

大多数情况下，人类将语言视为声音，当我们阅读时，我们主要是通过单词的声音和文本之间的反射运动来理解语言。阅读本身始于大脑枕极的视觉过程，学习阅读就是学习关注语音的不同音素，并将它们映射到字母上。广泛使用的 NLP 模型，如 BERT，只处理文本本身，与人类接收的允许他们理解语言的丰富多模态数据相比，接收的是完全扁平化的语言形式。这并不是说语言被人类理解为离散的符号单位，而是机器学习中使用的语言的表示被转换为连续的格式，一般是单词嵌入。

**2。人类使用语言在世界上行动**

语言模型(BERT、XLNET 等。)是基于利用从尝试预测记号中获得的洞察力。这种试图预测标记的尝试包括 NLP 模型建立语言的丰富表示(尽管不是对语言的理解)。例如，BERT 涉及两种主要的训练机制:屏蔽语言模型和下一句预测。第一个包括屏蔽一个标记并试图预测它(这就是为什么这个过程被认为是半监督的)，第二个包括试图预测一个句子是否跟随另一个句子。训练过程的这两个部分不仅要求网络通过掩蔽语言模型开发丰富的语义表示，还要求模型能够通过下一句预测理解文本的连贯性。相比之下，当人类学习时，他们的目的不是预测本身。他们试图在世界上行动，而语言是实现这一点的先决条件。我们对语言的理解可能取决于我们理解语言的目的，这不同于单纯的单词或下一句话的预测。

**3。不同比例加工**

人类不会一次读完整个单词。我们在世界范围内并行处理字母。虽然可以在字符、形态单元、音素、单词或更长的序列的级别上进行 NLP，但最常见的是在单词标记上进行 NLP。的确，字符级的 NLP 确实存在，CNN 可以用于字符级的处理。然而，还没有人类用来理解语言的词汇单位、单词和句子的多尺度理解。事实上，YOLO 是计算机视觉中的一个众所周知的模型，已经被用于处理多尺度的图像。也许这将是 NLP 未来的研究领域。

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)