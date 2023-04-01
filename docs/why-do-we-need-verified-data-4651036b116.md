# 为什么我们需要经过验证的数据

> 原文：<https://medium.com/mlearning-ai/why-do-we-need-verified-data-4651036b116?source=collection_archive---------11----------------------->

![](img/04d6fec856e7eb643a7ccab9ce0bd22c.png)

区块链项目世界面临的最重要的问题之一是虚假身份和声明的泛滥，以及由此导致的将有信誉的参与者与依靠欺诈和假冒的参与者区分开来的困难。这种情况的后果是严重的，从在加密项目中“从谷壳中挑选小麦”的低效率，到由假冒或与商业相关的直接欺诈导致的直接财务损失。假冒的个人资料、网站和令牌，冒充真实的、非法的团队成员、项目和令牌激增。或者，同样重要的是，合法的早期项目和投资者可能看起来不真实，甚至更糟，看起来像骗局。为了验证身份，并用区块链的**混合智能合同**取代依赖于各种业绩基准(里程碑、瀑布等)的传统风险投资投资和薪酬合同，重要的是要有**可靠的信息来源**来获取这些触发协议中各种条款的链外数据。由于此类数据的多个来源可以提供关于同一实体的不同数据，因此了解某一组数据的可靠性以及它是否可信非常重要。

有趣的是，目前企业界的数据集(如财务报表、法律协议、资产所有权、身份证件)由**验证机构**(会计师、律师、政府、银行)通过一种类似于区块链世界中所谓的“**赌注**”的遗留机制进行验证:当某人担保特定数据集的真实性，同时因提供此类参考而获得经济激励，并在数据受到质疑并被证明错误时承担经济损失的风险。例如，审计师提供财务审计是有报酬的。他们提供了数据真实性的证明，并以此来维护他们的“声誉”。但他们在现实中押下的不是他们的声誉，而是监管罚款和未来收入损失的潜在负面财务后果的价值(用区块链话来说就是“大幅削减”)。信息的可靠性是从验证者的可靠性/信誉中推断出来的。除了与数据验证者的声誉及其提供真实或虚假数据的历史**以及数据背后隐含的赌注**相关联的**之外，没有对数据的真实性进行衡量或排名的机制(例如，审计公司因不尽职而被吊销执照或向监管机构支付罚款的成本)。因此，由规模更大、经济上更强大的验证器进行的验证更有分量。**

聘请审计师(或律师)的过程漫长而繁琐，成本高昂，因此很少进行(通常一年一次)，只有产生可观收入的大公司才能负担得起(也必须如此)。在现代社会中，对于早期阶段的公司或更小且更多样化的公司数据块，没有方便的机制来做到这一点，因为当前的“标桩”机制非常低效。

但是区块链技术改变了这一点。它可以显著降低管理打桩过程的成本，并使其具有更广泛的用途。这将使能够提供赌注的人民主化，并向更广泛的代理人开放，这些代理人反过来可以提供对更多样化知识领域的访问。它还支持与数据验证相关的更复杂的关系，从而任何需要验证某段数据的实体都可以提供奖励来吸引验证者的服务。

基于上述认识， [KANDO 科技](https://kando.tech/)已经着手创建一个平台，用于存储和提供链上和链下的性能和身份数据(最初用于区块链和 crypto，以及风险创业项目)，这些数据通过一个涉及奖励、赌注和削减的分散机制生成和验证，其中每组数据都带有一个验证分数，允许数据用户(人或机器)对他们正在消费的数据的真实性进行可测量的评分。

我们打算验证的数据包括以下内容:

**唯一标识符**(用于实体解析):(I)注册(由政府当局和监管机构提供的唯一标识符)或“硬身份”。这种数据的例子包括公司注册号、SEC CIK、EIN 和其他类似的标识符；㈡非政府登记处的身份(例如 D & B 号)；(三)社交媒体简介(针对公司和个人)或“软身份”。通过使用应用编程接口(API ),这些身份还可以获取外部数据，例如关注者数量、最近的简档活动等；㈣其他静态数据(姓名、网站、地址、电子邮件、电话)；㈤链上数据(钱包、交易、智能合同)。

**业绩数据** : (i)财务业绩(由货币、会计准则和时间点或期间限定)，包括基于时间点的(资产负债表)和基于期间的(损益、现金流)；㈡投资业绩(内部收益率、资金倍数等)；㈢链外作业数据；(四)链上运营数据(与项目相关的钱包/用户/交易数量)。

关联事实 :(i)雇佣关系(公司和个人之间的关联，以及作为此类关联中次要标识符的职务名称)；㈡教育(公司和教育机构之间的联系，以及作为二级鉴定人学习的学位和学科)；㈢投资(一家公司与另一家公司或个人之间的关联)

在当前的“遗留”世界中，除了与数据验证者的声誉及其提供真实或虚假数据的历史相关联的**，以及数据背后的**隐含赌注**之外，没有对数据的真实性进行衡量或排名的机制(例如，审计公司因缺乏尽职调查而被吊销执照或向监管机构支付罚款的成本)。因此，由规模更大、经济上更强大的验证器进行的验证更有分量。相比之下，在我们的平台上，对于每一个需要验证的数据集，我们将能够提供一个定量值(赌注金额、赌注者数量，以及挑战金额和挑战者数量，如果未解决的话)，传达数据真实的可测量概率。**

作为一个副作用，我们也可以在此基础上构建应用程序。例如，经过验证的“声誉”的存在，对经济主体(在这里指投资者、投资目标、数字资产发行者)未来行为做出推断的能力，可以使该平台除了简单的数据验证之外，还有其他有趣的用途。为了证明这一点，KANDO 使用 API 访问数据库，为那些正在筹集资金的人建立了一个试验性的人工智能驱动的投资者识别引擎。其他类似的应用可以是识别合适的供应商、投资目标、人才等等。

我将在未来写更多关于我们项目各个方面的细节。同时，如果您想加入或支持它，请访问 [tokendata.app](https://tokendata.app/) 了解更多信息。

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)