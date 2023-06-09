# 非洲语言语音识别—语音到文本

> 原文：<https://medium.com/mlearning-ai/african-language-speech-recognition-speech-to-text-e2422c47549a?source=collection_archive---------1----------------------->

![](img/b06529bcfa10b5eb93fa4fe97160a430.png)

*来自 Dreamstime 的图片*

## 摘要

语音识别简单地说就是设备响应口头命令的能力。语音识别可以实现对各种设备和装置的免提控制(这对许多残疾人来说是一个特别的好处)，为自动翻译提供输入，并创建可供打印的听写。

在这个项目中，实现了端到端的非洲语言语音识别—语音到文本。从数据加载和元数据生成开始，一直到设计模型以预测和部署模型。

[我的 GitHub 链接](https://github.com/heavye/Swahili-Speech-To-Text)

## 动机

世界粮食计划署希望收集非洲两个不同国家——埃塞俄比亚和肯尼亚——市场上买卖的食物的营养信息。

该项目的特殊需求是，顽强数据科学咨询公司与世界粮食计划署(WFP)达成协议，为两种语言提供语音转文本技术:阿姆哈拉语和斯瓦希里语，使用一种应用程序，可以使用他们的声音激活应用程序，以他们自己的语言注册他们刚刚购买的商品列表。

> 为什么不使用现有的 ASR 系统呢？

有许多成熟的语音识别系统可用，如谷歌助手、亚马逊 Alexa 和苹果的 Siri。然而，所有这些语音助手都只支持有限的语言。

## 以前作品的评论

> 1.斯瓦希里语孤立数字语音语料库的开发

自动语音识别系统的开发-语音语料库是开发自动语音识别(ASR)系统的基本要求，为了提高系统的性能，它应该非常精确地完成。本文描述了为开发斯瓦希里语自动语音识别系统而从本地人和非本地人收集斯瓦希里语语音语料库时所要遵循的程序。

> 2.针对阿姆哈拉语语音识别的深度学习:

在这篇[文章](http://ainsightful.com/index.php/2018/11/27/deep-learning-for-amharic-speech-recognition/)中，核心思想是拥有一个互连节点的网络(也称为神经网络)，其中每个节点计算一个函数，并将信息传递给它旁边的节点。每个节点使用其配置使用的函数和一些参数来计算其输出。学习的过程更新这些参数。功能本身不会改变。最初，参数是随机初始化的。然后，训练数据通过网络传递，对每一步的参数进行小的改进。如果这一切看起来像魔术，你并不孤单！事实上，即使领先的研究人员在现场试验不同的功能和网络布局，看看哪一个工作得最好。有一些很好理解的功能和网络架构。在语音识别的情况下，使用递归神经网络(RNN ),因为其输出不仅取决于当前的输入集，还取决于先前的输入。这在语音识别中至关重要，因为如果知道之前说过什么，那么预测在特定时间窗口说过什么会变得容易得多。

## 数据和预处理技术

数据预处理是一个循序渐进的过程，为深度学习模型处理音频数据。下面列出了所使用的技术。

1.  加载音频文件:输入数据是音频格式的口语语音的音频文件。wav "

2.对音频文件进行重新采样，以便每个项目的采样速率一致。

3.将所有项目转换为具有相同数量的通道。声道可以是单声道(一个声道)或立体声(两个声道)。我们的数据是单声道的。

4.将所有项目转换为具有相同的时间长度，这涉及填充较短的音频文件和截断较长的音频文件。

5.将我们的音频随机向左或向右移动一个小的百分比，或者少量改变音频的音高或速度，以便向我们的音频文件添加噪声。

6.将原始音频文件转换为 Mel 频谱图，该频谱图通过将音频文件分解为多组频率，将音频文件的性质捕捉为图像。

7.梅尔频谱图被转换成梅尔频率倒谱 Coeﬃcients (MFCCs ),这在处理人类语音时很重要。这是因为 MFCCs 对应于人类说话的频率范围。

## 为转录准备元数据

我们使用 librosa 软件包对音频文件进行预处理。默认情况下，librosa 会将所有音频文件转换为单声道，并在加载音频文件时将文件重新采样为 22050 Hz，除非在 load 函数中传递了其他参数。现在我们有了输入特征(预处理音频文件)和目标标签(预处理转录)，我们构建了一个深度神经网络，它接受预处理数据作为输入，并返回口语的预测转录作为输出。

## 深度学习架构

卷积神经网络(CNN)加上递归神经网络(RNN): CNN 对来自语音特征的信息进行编码。该数据被发送到具有内核的卷积层，该卷积层也充当全连接层。这最终给出了可以放入转录中的每个字符的 softmax 概率

RNN 模型由双向 LSTM 组成，它将特征图作为一系列不同的时间步长或“帧”来处理，这些时间步长或“帧”对应于我们所需的输出字符序列。换句话说，它采用音频的连续表示的特征映射，并将它们转换成离散表示。

要素地图->双向 LSTM 使用 softmax 的线性图层，使用 LSTM 输出为位于卷积(CNN)和递归网络(RNN)之间的输出线性图层的每个时间步长生成字符概率。它有助于将一个网络的输出重塑为另一个网络的输入。

双向 LSTM ->线性层-> softmax ->频谱图中每个时间步长的字符概率 CNN 对来自图像的信息进行编码，并将该数据发送到基于 RNN 的解码器，该解码器对数据进行解码，并从图像中输出相应的文本。

## MLOPs 设置

MLOps 是一种 ML 工程文化和实践，旨在统一 ML 系统开发(Dev)和 ML 系统运营(Ops)。实践 MLOps 意味着您倡导 ML 系统构建的所有步骤的自动化和监控，包括集成、测试、发布、部署和基础设施管理。

## 建模结果和结论

> *1-真实转录:karibu katika matangazo yetu ya asubuhi ya idhaa ya Kiswahili*
> 
> *1-预测转录:karibu kaia natana zo yeti ya subu ia idha ya 斯瓦希里语*
> 
> *2-真实转录:kwenda na kuon doka jar kata Indonesia*
> 
> 2-预测转录:kuwenda kuna kundoka jijya kata indonezioaanfuyuhyhyya b

正如你所看到的，这个模型离完美还很远，但它正在接近完美。预测转录中的单词到处错位。对于一般可接受的语音识别系统，需要 3000 小时的录音。因此，对于这个数据有限的项目，模型预测相当成功。除此之外，为了使它更强大，模型可以有更多的隐藏层。

不同的说话者和文本需要更多的数据。数据也可以合成。例如，可以复制音频并将背景噪声添加到复制的数据中。它有助于模型在有噪声的音频上变得健壮。

此外，为了使模型更加稳健，我们可以对数据进行更多的扩充，添加噪声将提高模型在户外的稳健性，在这些地方最有可能实现项目的目标；这是一个食品市场，人们可能会使用该应用程序通过语音命令来注册他们购买的食品。

## 负责任的机器学习

> 原则偏见、公平性以及为缓解发现的问题所做的工作

当构建必须做出重要决策的系统时，我们将始终面临数据中固有的计算和社会偏见，这是无法避免的，但可以记录和/或减轻。

然而，我们应该后退一步，不要仅仅试图将伦理直接嵌入算法本身。相反，技术专家应该专注于建立流程和方法，以识别和记录数据、特征和推理结果中的固有偏差，以及随后这种偏差的含义。

**样本偏差:**样本偏差是训练数据的一个问题，当用于训练模型的数据不能准确表示模型将在其中运行的环境时，就会出现这种问题。实际上，没有任何情况下，算法可以在它可以与之交互的整个数据世界上进行训练。但是选择一个足够大和足够有代表性的宇宙子集来减轻样本偏差是有科学依据的。

**评估偏差:**评估偏差发生在模型迭代和评估过程中。使用训练数据来优化模型，但是它的质量通常是根据某些基准来衡量的。当这些基准不代表一般人群或不适合模型的使用方式时，就会产生偏差。

**聚集偏倚:**聚集偏倚出现在模型构建过程中，不同的人群被不恰当地组合在一起。在许多人工智能应用中，感兴趣的群体是异质的，单一模型不可能适合所有群体。一个例子是卫生保健。为了诊断和监测糖尿病，模型在历史上使用血红蛋白 AIc(hba1c)的水平来进行预测。然而，2019 年的一篇论文显示，这些水平在不同种族之间以复杂的方式存在差异，适用于所有人群的单一模型注定会出现偏差。

**公平性:**有助于确保数据中的偏差和模型的不准确性不会导致模型根据种族、性别、残疾、性取向或政治取向等特征对个人进行不利的对待。

**数据风险意识:**我们致力于开发和改进合理的流程和基础设施，以确保在开发机器学习系统的过程中考虑到数据和模型的安全性。

## 未来的工作

> **用更多的时间和资源可以改进什么？**

**数据&型号**

3k 小时的演讲曾经被认为是训练的 suﬃcient。大型科技公司现在使用高达 10 万小时和强大的硬件。斯瓦希里语和阿姆哈拉语只有有限的几个小时的数据。不同的说话者和文本需要更多的数据。数据也可以合成。例如，可以复制音频并将背景噪声添加到复制的数据中。它有助于模型在有噪声的音频上变得健壮。

我们已经向自己证明，该模型能够拟合提供给它的训练数据。下一步是研究正则化，以获得良好的验证准确性。这个问题也可以受益于更多的数据。也可以研究不同的网络架构。正如在语言模型中提到的，目标是进行端到端的培训。所以我们甚至不需要任何预处理。百度 2 通过使用声谱图特征，在这个方向上走了一步。也有一些关于使用音频信号(原始数据)的研究，尽管它仍处于起步阶段。

参考

1.  https://citeseerx.ist.psu.edu/viewdoc/download?doi = 10 . 1 . 1 . 402 . 5170 & rep = re P1 & type = pdf

2.https://towards data science . com/audio-deep-learning-made-simple-automatic-sp eech-recognition-ASR-how-it-works-716 cfce 4c 706

3.http://ainsightful . com/index . PHP/2018/11/27/deep-learning-for-amharic-speech recognition/

4.https://ethical.institute/principles.html

感谢您的阅读😊

Euel Fantaye，2021 年 8 月