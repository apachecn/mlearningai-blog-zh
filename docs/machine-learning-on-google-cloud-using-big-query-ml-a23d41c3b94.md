# 使用大查询 ML 在 Google Cloud 上进行机器学习

> 原文：<https://medium.com/mlearning-ai/machine-learning-on-google-cloud-using-big-query-ml-a23d41c3b94?source=collection_archive---------2----------------------->

## 使用大查询 ML 在 MNIST 数据集上训练和评估分类模型

![](img/1fd9cf23682045175f32907e60c541fe.png)

Photo by [Robynne Hu](https://unsplash.com/@robynnexy?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

谷歌、亚马逊和微软等顶级云计算平台已经进行了大量投资，并在人工智能和机器学习的民主化上下了大赌注。最重要的是，越来越多的公司采用机器学习来提高盈利能力，并通过改善业务流程来更好地服务于客户。

公司发现使用云平台提供的 ML 选项更容易实验和测量他们的机器学习能力，因为这些工具主要是为了让每个人都可以使用人工智能和 ML 技术而开发的。因此，公司不需要等到拥有高级人工智能技能的成熟数据科学家团队建立起来。相反，他们可以利用现有资源开始实验和 ML 建模。

## 这个系列涵盖了哪些内容？

在这一系列的三个故事中，我将向您介绍在 GCP 上执行机器学习的三种不同方式。我们将使用 GCP 提供的以下 ML 选项在 MNIST 数据集上训练和评估分类模型。然后，我们将使用我们训练的模型来正确预测 MNIST 测试数据集上的手写数字。

**本系列探讨的 ML 选项:**

*   大查询 ML(在这个故事中涉及)
*   [汽车视觉(第二部)](https://hshirodkar.medium.com/machine-learning-on-google-cloud-using-automl-vision-88e16abf986e)
*   [定制模型使用 Keras(第三个故事)](https://hshirodkar.medium.com/machine-learning-on-google-cloud-using-the-ai-platform-custom-model-ab0cbc874388)

## Google 提供的免费试用积分:

谷歌将向其新客户提供 300 美元的免费试用信贷，以全面探索和评估其谷歌云平台。这是获得谷歌人工智能产品实践经验的好方法。

## **先决条件:**

*   **机器学习的基本概念:** 本教程更侧重于理解如何利用 GCP 来执行机器学习，而不是学习 ML 概念。
*   **Google Cloud 帐户:** 如果您还没有帐户，请在 [Google Cloud](https://cloud.google.com) 上注册一个新帐户。
    一旦您的帐户设置完毕，请使用 GCP 控制台的导航菜单并转到账单页面。账单概览页面应显示应用于您帐户的 300 美元试用信用(我在截图中看到了额外的信用，但您的帐户在首次注册时应显示 300 美元)。**请确认您拥有必要的学分，然后再继续本教程的剩余部分，否则将会产生费用。**

![](img/c307bd7c748e1608d61a847fcf36a474.png)

“账单”下的概览页面应显示已应用于您帐户的点数。

![](img/9eab34007ae8769e2a47f17d630ea3af.png)

## 什么是 MNIST 数据集及其在本系列中的用途？

MNIST 是机器学习爱好者中非常受欢迎的数据集，当谈到学习真实世界数据的新建模技术时，没有数据预处理要求。数据一开始就结构良好，易于理解。我个人更喜欢使用 MNIST 数据集，这样我们可以专注于手头的任务，学习 GCP 提供的 ML 选项，而不是被数据集本身的复杂性分散注意力。

> MNIST 数据库(改进的国家标准和技术研究所数据库[1])是手写数字的大型数据库，通常用于训练各种图像处理系统。
> 
> 数据文件 mnist_train.csv 和 mnist_test.csv 包含手绘数字的灰度图像，从 0 到 9。
> 
> 每幅图像高 28 像素，宽 28 像素，总共 784 像素。每个像素都有一个与之关联的像素值，表示该像素的亮度或暗度，数字越大表示越暗。该像素值是 0 到 255 之间的整数，包括 0 和 255。
> 
> 训练数据集(mnist_train.csv)有 785 列。第一列称为“标签”，是用户绘制的数字。其余的列包含相关图像的像素值。
> 
> 测试数据集(mnist_test.csv)与训练集相同，只是它不包含“标签”列。

## **大查询 ML:**

> **什么是 BigQuery？**这是一个企业数据仓库，利用谷歌基础设施的处理能力，在海量数据集上实现超快速的 SQL 查询。
> 
> **什么是 BigQuery ML？**它让你使用标准的 SQL 查询在 BigQuery 中创建和执行机器学习模型。主要目标是通过让 SQL 从业者使用现有的 SQL 工具和技能来构建模型，从而使机器学习民主化。[大查询 ML 支持的当前模型可以在这里找到。](https://cloud.google.com/bigquery-ml/docs/introduction)

## **步骤 1:下载 MNIST 训练和测试数据集。**

为了加快训练速度，我们将只使用原始 MNIST 数据集的一个子集。继续从本地机器上 git 存储库内的 ML 文件夹中下载 MNIST 训练(mnist_train.csv)和测试(mnist_test.csv)数据集。[这里是 GitHub 的链接。](https://github.com/crazycoder20/MLonGCP/tree/main/ML)

## **步骤 2:创建一个云存储桶并上传 MNIST 数据集。**

从项目仪表板中，**复制项目 ID** 。我们将使用这个项目 ID 来设置一个全球唯一的云存储桶，以上传 MNIST 数据集。

![](img/f31df0c0ca0d9a05234ff433bdeec09a.png)

从导航菜单中，选择**云存储，然后点击浏览器。**

![](img/512066fd829620409444fcf0f8757a83.png)

**点击创建桶。**

![](img/8075eba72c5a030fccf0fa158514f8c8.png)

使用<**ProjectID**>**-ml**作为您的存储桶和离您最近的地区的名称。对存储类别、访问控制和高级设置使用默认值。

![](img/ad364c1e47188afc1e1b3af7e398dca4.png)![](img/5c943ab48a7f49b9e0a93be05a3aff5b.png)

**点击创建。**

![](img/57f98f0b4ffc40d93bcd52fc63b578ca.png)

Click on CREATE.

一旦创建了 CS bucket，**点击上传文件**从您的本地机器中选择 mnist_train.csv 和 mnist_test.csv。

![](img/1bafa7984f66b5c22b2649f5259390e6.png)![](img/fb71dfb5d831d5e187a554ca661bf556.png)

文件上传后，CS bucket 应该如下所示:

![](img/3f42d6023df04e80de8cc49b0a6acffb.png)

## **第三步:将 MNIST 数据集从云存储上传到大查询。**

从导航菜单中，向下滚动到**选择大查询**。您可以选择锁定产品，以便将来更快地查找。

![](img/2efdbf092349915501c6761c53c815a8.png)

从左侧菜单中选择您的项目，然后点击**创建数据集。**数据集类似于大查询的数据库。

![](img/6863e4cc2e30a7906108e6aabc16a1a4.png)

给 **mnist** 作为数据集 ID，位置与您的云存储桶相同。将其他选项保留为默认选项，并点击**创建数据集**。

![](img/85af1604a1af64ed07ec7c7b9833eebd.png)

一段时间后，在左侧菜单面板上，您应该看到在您的项目下创建的数据集 mnist。

现在，我们有了数据集，是时候创建表来保存这些文件了。我们将创建两个单独的表，一个用于训练数据集，另一个用于测试数据集。

**点击创建表格**从 CS 上传训练数据集。

![](img/a8156759635dacf51f474215f3342748.png)

在下一个屏幕上，请选择以下选项，然后单击创建表格。

*   **Source** :选择 Source 为“ **Google Cloud Storage** ”，并为训练数据集提供 GCS bucket 的位置(使用 browse 选择文件)。文件格式为 csv。
*   **目的地**:提供表名为**车次**。
*   **模式**:勾选自动检测框。

![](img/462aab9c209ecd38fe13f062fb40a2dc.png)

按照相同的步骤创建测试表。

![](img/7c6ce27f07f43b45dc2b683db4bac8c8.png)

一旦数据集被加载，训练和测试表应该显示在 mnist 数据集下。

选择列车表并**点击预览**。在这里花点时间熟悉一下数据。该表上的每一行都是来自训练数据集的实例，并带有相应的标签。

![](img/dcd32244a0c754c4e4fe2402283429d1.png)

您可以在查询编辑器中运行以下查询，该查询提供了每个标签的训练数据集中的样本数。只需将 from 子句中的<project-id>替换为仪表板中的项目号。</project-id>

训练数据集总共有 6000 个样本。这些或多或少均匀分布在标签上。

![](img/5778cd5aac522df118989040206e2835.png)

我们现在准备好运行我们的分类模型了！

## 第四步:使用逻辑回归训练模型。

> 逻辑回归是一种监督学习分类算法，用于使用成本函数(如 Sigmoid)预测目标变量的概率。

通常，逻辑回归用于二元分类问题，其中只有两种可能的结果(例如:电子邮件是垃圾邮件还是不是垃圾邮件)。

但是，在这个故事中，我们将使用它来训练一个多类预测模型。共有 10 个类别，从 0 到 9 的每个数字一个类别。

再次将上述查询粘贴到编辑器中，然后单击 Run 来训练模型。大约需要。5 分钟让 BigQuery ML 训练你的模型。

![](img/ec51d9de55e7399b5c319093ca37f509.png)

一旦模型被训练，它将作为“分类 _ 模型”被添加到您的 mnist 数据集中。单击它查看模型详细信息。聚合指标在评估中提供。

![](img/5e2b41959f49ba7ab29c563f56dea080.png)

基于 ROC AUC 评分，结果相当有希望。你的结果可能与我的不完全相同，但应该足够接近。

向下滚动查看混淆矩阵。

![](img/bd08155d71996a0f0e2150dba6d09b6f.png)

使用混淆矩阵，我们可以观察到该模型在某些标签上比其他标签表现得更好。它在 1 号和 6 号上表现很好。预测数字 5 肯定需要改进，我们可以通过添加更多数据或试验其他模型参数来实现，但这将是另一天的讨论主题。

> ROC 曲线代表受试者操作特征曲线，通常与二元分类器一起使用。ROC 绘制了真阳性率对假阳性率的曲线。
> 
> 您可以通过测量两个分类器的 ROC 曲线的 AUC(曲线下面积)来比较分类器。完美分类器的 ROC AUC 等于 1，而纯随机分类器的 ROC AUC 等于 0.5。
> 
> 混淆矩阵用于**评估分类器的性能。**一个完美的分类器将只有 TPs 和 TNs(对角线值)

![](img/2b734c64ac0aa27c8e2e54969e5a983c.png)

Confusion Matrix

## **第五步:是时候做一些预测了。**

我们将使用新训练的模型对测试数据集进行预测。请注意，我们的模型在训练期间从未暴露给测试实例。

在编辑器中运行下面的查询。

![](img/916a087a6bf69a2f33e0ed18301b3ee9.png)

查询完成后，**点击结果**查看预测。

在下面的屏幕截图中，测试数据集中的第一个实例被正确预测为 0。如概率分数 0.998 所示，该模型对此预测具有非常高的置信度。如果你仔细观察，你会发现这个模型也给了我们预测其他标签的概率分数，在这个例子中这个分数相当低。

![](img/6e0a500765a27de97a92b63424c41d46.png)

## 第六步:删除大查询数据集和云存储桶。

完成评估后，请继续删除大型查询数据集和云存储空间，以避免任何成本。

在下面的屏幕上，选择 mnist 数据集，然后点击**删除数据集**。确认数据集已被删除。

![](img/05a34e4f595644e89fbb7c22e97a6e21.png)

同样，进入云存储控制台，选中<projectid-ml>桶的复选框，然后**点击删除**。确认该存储桶不再存在。</projectid-ml>

![](img/946054e04d1fffb89ee3c266a93d02ea.png)

## 结论:

我们只是触及了表面，但是您可以随时使用 Big Query 提供的其他公共数据集进行实验。像 Big Query ML 这样的产品无疑让我们在大众化机器学习方面更进了一步，我完全同意！

以下是本系列其他两个故事的链接:

*   [使用 AutoML 视觉在谷歌云上进行机器学习](https://hshirodkar.medium.com/machine-learning-on-google-cloud-using-automl-vision-88e16abf986e)
*   [使用人工智能平台在谷歌云上进行机器学习(定制模式)](https://hshirodkar.medium.com/machine-learning-on-google-cloud-using-the-ai-platform-custom-model-ab0cbc874388)

## 提醒一句:

请小心使用谷歌云上的服务，不要超出 300 美元的试用预算。不要忘记关闭 API，删除任何未使用的实例或在使用后清理云存储桶，以避免向您的帐户收取任何额外费用。