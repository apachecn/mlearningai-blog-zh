# 方位和光照对人脸识别系统的影响

> 原文：<https://medium.com/mlearning-ai/effect-of-orientation-and-illumination-on-facial-recognition-system-cc234ab22431?source=collection_archive---------1----------------------->

![](img/2c470ecef24395fd4ad3bf3a2352785d.png)

[a photo of light and mask // generated by art.MLearning.ai](https://www.hicetnunc.xyz/objkt/41700)

## 方位变化对人脸识别系统的影响

面部特征会随着光照和方向发生剧烈变化，导致错误拒绝和错误接受的增加，我们无法存储同一个人在不同角度和光照下的图像。如果我们这样做，那么我们将导致数据库过载[1]。75%的面部识别系统认证失败，这是由于测试面部图像的方向与存储图像的方向不同[1]。所以，我们需要一些对方向变化不变的特征。

在[2]中，他们选择了 9 个具有角度不变性的特征点，分别是 2 个眼球、4 个远近眼角、鼻孔中点和 2 个嘴角。他们选择了算子 SUSAN 来提取局部特征区域的边缘和角点。在[3]中，它以不同的角度拍摄多个图像，保持相机和对象之间的距离，并使用相同的照明。这里，旋转范围被认为是从-60°到+60°，并且使用 12 PCA。欧氏距离用于相似性匹配，但配准和测试图像。角度特征向量包含 6 个元素。在[4]中，他们认为鼻子是面部的定位部件。鼻尖对应于最亮的灰度级。他们考虑的特征是眼唇距离、眼鼻距离、鼻唇距离、角眼唇、角眼鼻和角鼻唇。在[5]中，局部线性回归预测非正面人脸图像的正面图像，Fisher 线性判别分析进行人脸识别，在识别之前使用主成分分析(PCA)对人脸图像进行降维。

在[1]中，方法是在单个训练的 MLP 中存储多个姿态图像特征，使得中间角度的存储和搜索都是有效的，并且没有数据库过载。几何特征对于角度变化是脆弱的，因此他们使用几何特征的子集来表示姿态。他们的目标是以较低的计算复杂度提取角度特征。为了识别面部的重要特征，它使用 2 个滤波器最小值滤波器和二值化。他们使用了左右眼位置和嘴中间的 3 个点。它们之间的距离和连接它们的线的斜率被用作特征向量的元素，因此在作为 MLP 输入的角度特征向量中有 12 个元素五个距离和四个线梯度。对于图像特征提取，他们使用了 IDA。神经网络被用作映射函数。由于有 12 个角度特征，所以在该模型中存在 12 个输入节点和 16 个隐藏单元和 8 个输出单元，相当于没有使用 IDA 提取图像特征。他们对每个个体使用单独的 MLP，并且对于训练图像，他们以-50 到+50 度的方向角以 5 度的间隔拍摄每个个体的图像。它们有 21 幅训练图像，其中 11 幅是在 50°、40°、30°、20°、10°、0°、+10°、+20°、+30°、+40°和+50°方向拍摄的。在 45°、35°、25°等角度方向上为 10°。因此，得到了很好的推广。这导致了良好的错误接受率(FAR)以及错误拒绝率(FRR)。文献[6]在 DP-Adaboost 算法中设计了正面人脸分类器和侧面人脸分类器的分类器融合来检测多角度人脸。在 DP-Adaboost 算法中提出了一种改进的水平差分投影方法来去除检测结果中的虚假人脸。

**改变光照对面部识别系统的影响**

许多技术被引入来解决照明问题，如照明锥方法[7]和 9 D 线性子空间[8]，但它们需要大量的数据和光源知识。因此，为了解决这个问题，引入了基于区域的图像提议方法[9]。还介绍了一些照明归一化方法，如多尺度 retinex [10]、基于小波的归一化技术(WA) [11]和基于 DCT 的归一化技术[12]。在[13]中，介绍了一种称为均值估计法的光照归一化方法。在这种照明中，通过从原始图像中减去平均估计来去除该分量。为了标准化不同人脸图像的整体灰度，获得商图像与其模均值的比值矩阵。由于面部器官的灰度值小于面部皮肤的灰度值，所以对图像进行后处理，使得人脸识别的焦点集中在面部纹理上。这个方法给了我们很好的结果。本文[14]介绍的光照归一化技术使用直方图归一化方法，该方法通过改变原始像素的值来增加图像的对比度，因为 PCA 和 LDA 对光照敏感，并且 LDA 的属性通过改变人脸图像的像素值而被破坏。在[15]中，该方法基于二维经验模式分解，并使用梯度人脸算法来处理变化光照下的人脸图像。人脸图像的两个 IMF 在对数域进行分解。然后，采用梯度人脸增强重构后人脸图像的高频分量。使用主成分分析提取人脸特征，使用基于余弦距离的 KNN 分类器进行分类。在[16]中，直方图均衡化、梯度人脸和韦伯人脸方法用于归一化人脸图像的光照，并且通过使用中心对称局部二进制模式、局部二进制模式、局部方向模式、局部相位量化、旋转局部二进制模式和局部三进制模式描述符来进行特征提取，并且 SVM 用于分类。在[17]中，他们介绍了基于 Gabor 相位的光照不变提取方法。通过首先使用基于同态滤波器的预处理方法来归一化人脸图像，以消除光照变化的影响。然后，用一组不同方向的 2D 实 Gabor 小波进行图像变换，同时考虑频谱和相位，将多个 Gabor 系数合成一个整体。最后，从组合系数中提取相位特征，得到光照不变量。在[18]中，他们使用 ICA 来消除图像中的光照影响。

**参考文献:**

[1]加藤，Hisateru & Chakraborty，古塔姆& Chakraborty，巴萨比。(2012).基于人工神经网络的实时角度和光照感知人脸识别系统。应用计算智能和软计算。2012.10.1155/2012/274617.

[2]，苏，程光达。(2003).人脸的特征点提取。

[3] B. Chakraborty，“一种新的基于人工神经网络的角度不变人脸验证方法”， *2007 年 IEEE 图像和信号处理计算智能研讨会*，檀香山，HI，2007，第 72–76 页，doi: 10.1109/CIISP.2007.369296

[4] Kavita S.R .，Mukesh z . a .，Mukesh R.M. (2010)姿势不变面部特征的提取。载于:Das V.V .，Vijaykumar R. (eds)信息和通信技术。ICT 2010。计算机与信息科学通讯，第 101 卷。施普林格，柏林，海德堡

[5]柴，秀娟&山，&陈，西林&高，文.(2007).姿态不变人脸识别的局部线性回归。IEEE 图像处理汇刊:IEEE 信号处理学会的出版物。16.1716–25.10.1109/小费

[6]郑，张莹莹，姚军(2015).基于 DP-Adaboost 的多角度人脸检测。国际自动化与计算杂志。12.10.1007/s 11633–014–0872–8。

[7] J. Ho、M.-H. Yang、J. Lim、K.-C. Lee 和 D. Kriegman，“不同照明条件下物体的聚类外观”，IEEE 计算机学会计算机视觉和模式识别会议论文集，第 11-18 页，美国威斯康星州麦迪逊，2003 年 6 月

[8] R. Basri 和 D. W. Jacobs，“朗伯反射和线性子空间”，IEEE 模式分析和机器智能汇刊，第 25 卷，第 2 期，第 218-233 页，2003 年。

[9] G. An、J. Wu 和 Q. Ruan，“不同光照条件下人脸识别的光照归一化模型”，《模式识别通讯》，第 31 卷，第 9 期，第 1056-1067 页，2010 年。

[10] D. J. Jobson、Z.-U. Rahman 和 G. A. Woodell，“一种多尺度 retinex，用于弥合彩色图像和人类对场景的观察之间的差距”，IEEE 图像处理汇刊，第 6 卷，第 7 期，第 965-976 页，1997 年。

[11] S. Du 和 R. Ward，“用于人脸识别的基于小波的光照归一化”，载于 IEEE 图像处理国际会议(2005 年 ICIP)论文集，第 2 卷，第 954-957 页，意大利热那亚，2005 年 9 月。

[12] W. Chen、M. J. Er 和 S. Wu，“使用对数域中的离散余弦变换进行鲁棒人脸识别的光照补偿和归一化”，IEEE 系统、人和控制论汇刊 B，第 36 卷第 2 期，第 458-466 页，2006 年。

[13]罗，永&关，叶鹏&张，常启.(2013).基于均值估计的人脸识别鲁棒光照归一化方法。ISRN 机器视觉。2013.1–10.10.1155/2013/516052.

14 Shah，Jamal & Sharif，Muhammad & Raza，Mudassar & Murtaza，Marryam & Ur Rehman，Saeed。(2015).光照变化下的鲁棒人脸识别技术。应用研究与技术杂志。13.97–105.10.1016/s 1665–6423(15)30008–0。

[15]杨，何志军，薛，熊，聂文义，向飞.(2016).基于格林函数的二维经验模式分解和梯度脸的人脸识别。ITM 会议网。7.01015.10.1051/itmconf/20160701015。

[16] Tran，Chi-Kien & Tseng，Chin-Dar & Chao，Pei-Ju & Shieh，Chin-Shiuh & Chang，& Lee，Tsair-Fwu .(2017).不同光照条件下的人脸识别:结合韦伯人脸和局部方向模式进行特征提取和支持向量机进行分类。信息隐藏与多媒体信号处理杂志。8.1009–1019.

[17]范，王春年，王平，张，郝.(2017).用于人脸识别的高效 Gabor 相位光照不变量。多媒体的进步。2017.1–11.10.1155/2017/1356385.

[18] Ahmad、Fawad & Khan、Asif & Islam、Ihtesham & Ullah、Habib。(2017).使用独立分量分析和滤波的光照归一化。影像科学杂志。1–6.10.1080/13682199.2017.1338815.