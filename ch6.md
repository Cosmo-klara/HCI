# Hypothesis Testing

在鸡尾酒会上，最好避免讨论宗教或政治。原因当然是人们对这些棘手话题的意见往往既强烈又分歧。让我们再加上统计学。几乎没有什么话题能比在实验研究中将统计技术应用于数据和假设更能引起争议了。幸运的是，读者并没有被卷入这场争论。相反，本章将描述并介绍人机交互研究中通常使用的一些有用的统计工具和技术。在接下来的篇幅中，我将努力将理论和争论最小化，同时将实用价值最大化。

假设检验的统计程序有两种：参数检验和非参数检验。本章将对这两种方法进行研究。它们的显著特点是：参数检验对来自概率分布（如正态分布或 t 分布）的数据进行检验，而非参数检验是 "无分布 "的，也就是说，它们对基础数据的分布不做任何假设。区分参数检验与非参数检验的有效方法是根据被检验数据的测量水平或尺度（Sheskin，2011 年，第 109 页；Siegel，1957 年，表 1）。图 6.1 举例说明。图中显示了第 4 章（见第 4.4.2 节）中讨论的四种测量尺度，其中比率数据最复杂，名义数据最不复杂。

参数检验适用于比率数据和区间数据，但最常用于比率数据。本章将详细讨论的方差分析（ANOVA）是最广泛使用的参数检验方法。 

![ ](./img/22.png)

在人机交互的实验研究中，比值数据通常是人类性能的测量值，如完成任务的时间、速度或准确性，或事件计数，如按键、手指弹动、视线移动或目标重入。非参数检验适用于任何规模的数据，尽管它们最常用于名义或序数数据。本章研究的非参数检验方法包括用于名义数据的卡方（χ2）检验和用于序数数据的曼惠尼 U 检验、威尔科克森符号秩检验、克鲁斯卡尔-瓦利斯检验和弗里德曼检验。通常，非参数检验使用的数据是名义类别、问卷回答、评级分数或量表评估。对于比率数据，非参数检验的使用很有限，我们将在本章稍后讨论。

由于非参数检验被认为与所有四个测量量表相关（见图 6.1 右栏），因此它们比参数检验更普遍适用。然而，根据功率标准，参数检验优于非参数检验。这是参数检验的强假设和强要求的副产品。只要假设得到合理的遵守，参数检验就有更大的能力（功率）在所进行的统计检验中得出正确的结论。

本章的大部分内容都是针对方差分析的。然而，大多数使用方差分析的研究人员对方差分析中 "F 检验 "的计算和假设了解甚少。这也没有关系。不过，了解检验的含义、如何进行检验以及如何解释和说明检验结果是非常重要的。因此，我们在这里采用的方法更像是教科书，而不是学术性的

##  6.1 Analysis of variance

方差分析或 F 检验是因子实验中进行假设检验的主要统计程序。大多数描述实验的人机交互研究论文都包含方差分析结果，给出 F 统计量、F 统计量的自由度以及相关的 P 值（稍后解释）。方差分析结果通常在括号中报告，以支持说明 检验结果是否具有统计学意义。

方差分析确定自变量（测试条件）是否对因变量（测得的反应）有显著影响。方差分析通过将因变量观测值的方差划分为可归因于方差的各个部分来确定。可归因的成分 "是测试条件（因子和水平）和参与者。如果一个因子在不同水平上的方差相对于所有其余方差（其他因子和参与者）较大，那么通常可以得出结论：该因子的显著特性--测试条件中的特征--导致了因变量测量结果的观测差异。如果是这样，就可以说该因素对因变量产生了具有统计学意义的影响。

根据实验设计的不同，方差分析有不同的设置方法。本讨论从具有两个测试条件的简单单因素设计开始。然后，我将讨论具有四个测试条件的单因素设计。如果有两个以上的测试条件，通常会使用事后比较检验，我也会举例说明。然后，我将讨论包含两个或更多因素的更复杂的设计，每个因素都有两个或更多水平。

最初的示例假定在受试者中分配测试条件。这意味着每个参与者都要接受某一因素所有水平的测试。有些设计的测试条件是在受试者之间分配的，即招募一组单独的参与者，并将其分配给每种测试条件。下面还给出了几个主体间方差分析的例子

### 6.1.1 Why analyze the variance?

我在前面提到，研究问题通常是比较性的。通常，研究的目的是比较两种或两种以上的界面或交互技术，以确定哪种更好。我所说的 "更好 "是指在一个或多个因变量上的优异表现，如任务完成时间、错误率、任务重试次数、退格键的按下次数、目标重试次数等。有趣的是，这项测试被称为方差分析，但我们更关心的是总体表现：

![ ](./img/23.png)

上面的问题指的是时间--观察和测量的总体、平均时间。平均值是针对多个用户的每个测试条件计算出来的，通常是针对一项代表性任务的多次试验计算出来的。在某些情况下，对一项任务进行多次试验是为了调查学习效果（见第 4 章，纵向研究），但使用多次试验的目的往往只是为了获得稳定和有代表性的测量结果。不过，我们感兴趣的是平均值的差异，而不是方差。请注意，上述研究问题固然重要，但所追求的统计问题根本不是问题。它是一个被称为 "零假设 "的陈述：

![ ](./img/24.png)

假设 "无差异"，这是一个合理的起点。方差分析对数据进行检验，以确定零假设为真（成立）或为假（被拒绝）的可能性。在大多数情况下，研究人员会设法拒绝零假设。按照惯例，统计上显著的结果意味着零假设为真的可能性很小。这种情况下的结论是：(a) 均值存在差异；(b) 差异在统计上显著；(c) 差异是由试验条件中的可区分特性造成的。让我们来看看如何做到这一点。

假设有这样一个实验：10 名参与者使用两种交互技术重复完成一项任务。交互技术可以是任何技术，例如使用鼠标和键盘。实验选择的任务既能代表常见的交互方式，又有可能暴露出内在的差异。鼠标与键盘交互的例子可能是在分层菜单中选择选项。在本讨论中，我将保持简单明了，将这两种技术分别称为方法 A 和方法 B。请记住，本实验只有一个因素（交互方法）和两个水平（方法 A 和方法 B）。

![ ](./img/25.png)

成绩是根据任务完成时间（以秒为单位）等因变量来衡量的，并计算出每个参与者在几次试验中的平均值。然后计算每种方法的平均值。图 6.2 中的条形图显示了这一假设实验的两个结果示例。

在图 6.2a 和图 6.2b 中，任务完成的平均时间相同；但是，标注的结果却大相径庭。在图 6.2a 中，平均值的差异在统计学上是显著的。这意味着观察到的差异很可能是真实的，是由于方法 A 和方法 B 的不同特性造成的。

在图 6.2b 中，平均值的差异在统计上并不显著。这意味着平均值的差异很可能是偶然造成的。没有合理的依据表明任何一种方法都比另一种方法快。再做一次测试，结果很可能相反。尽管解释大相径庭，但这两个例子似乎是一样的：方法 A 的任务完成时间为 4.5 秒，而方法 B 为 5.5 秒。答案就在于观察结果的差异性--方差。让我们仔细看看。

![ ](./img/26.png)

图 6.3a 给出了图 6.2a 中的模拟数据，即每位参与者使用每种方法完成任务的平均时间（以秒为单位），以及每种方法的总体平均值和标准偏差。图 6.3b 显示了相应的柱形图，并带有误差条。误差条显示平均值的 ±1 个标准差。在数学上，方差是标准偏差的平方；然而，在研究论文中，报告标准偏差更为常见，因为标准偏差和平均值的单位相同（本例中为 "秒"）。

![ ](./img/27.png)

对图 6.3a 中的数据进行方差分析的步骤取决于所使用的统计程序。尽管如此，结果还是与图 6.4 中的表格相似。
   
表中最重要的统计量是 "P 值"。这是在零假设成立的情况下获得观测数据的概率。概率低，说明根据零假设，不可能出现均值差异。高概率表明均值差异可能只是偶然因素造成的。当 p = 0.0121 时，有一个相当低的概率--小于 2%--即差异仅仅是一个偶然的结果。很有可能是一种或另一种方法的某些固有的显著特性造成了差异。请注意前一句中的 "造成 "一词。实验研究之所以如此有价值，原因之一就是可以得出因果关系的结论。

根据实验研究的惯例，统计学意义上的显著性要求 p 小于 0.05，即 20 分之 1 的概率。换句话说，我们认为零假设是成立的，除非有 20 分之 1 或更小的概率认为零假设是不成立的。除了概率，方差分析中的重要统计量还有 F 统计量（F 值，样本方差的比率）以及主效应（方法）和残差效应（方法 * 主体）的自由度。相关统计数据汇集成一份声明，宣布研究问题的结果。

![ ](./img/28.png)

图 6.5（F 四舍五入到三位有效数字）是假设实验的研究论文中可能出现的示例。请注意，图中没有精确引用概率。相反，p 被引用为小于集合 {.05，.01，.005，.001，.0005，.0001}中一个更保守的临界值。因此，p 被引用为 p < .05 而不是 p = .0121.6。

图 6.5 中的语言包括测试条件的均值和均值差异的说明。平均值的差异就是效应大小。在人机交互研究中，效果大小通常是通过给出均值和绝对差值（本例中为一秒）或相对差值来表达的。当然，效果大小是否具有实际意义并不在方差分析的范围之内。在研究论文中，F 统计量的格式往往很不规范，因此值得稍作停顿，观察一下图 6.5 中的 F 统计量：

+ 放在括号内

+ F 大写

+ p 为小写

+ F 和 p 为斜体

+ 等号两边的空格

+ 逗号后的空格

+ 小于号两侧空格

+ 自由度为下标、普通、较小的字体8

+ F 统计量为三或四位有效数字

+ P 统计量小数点前没有零（因为它被限制在 0 和 1 之间）

For completeness, let’s study the second example, the simulation in Figure 6.2b. The data and corresponding bar chart embellished with error bars are shown in Figure 6.6.

![ ](./img/29.png)

As noted earlier, the results for the second simulation are not statistically significant. A hint of this is the large error bars in Figure 6.6b. The ANOVA reveals and confirms the lack of significance with a high value in the p statistic. As evident by the P-value in Figure 6.7, there is about a 45 percent chance the difference in the  means is simply a chance outcome. Even though the means are the same as in the first simulation, there was such a large variation in the performance of participants that the difference in the means between the test conditions may simply be due to chance. Observe in Figure 6.6a, for example, that participant #8 completed the task in 1.2 seconds using Method A while participant #10 took 6.6 seconds. Evidently, there is something going on that falls outside the explanatory power of the two interaction methods under test.

![ ](./img/30.png)

In a research paper, non-significant results are also important to report. Figure 6.8 is an example for the second simulation. Bear in mind that a non-significant ANOVA does not imply that the null hypothesis is true (i.e., no difference in the means). A non-significant ANOVA simply indicates that the evidence is insuff icient to reject the null hypothesis: The null hypothesis remains tenable.

![ ](./img/31.png)

For non-significant results, the ANOVA result is reported in one of two ways. If F is less than 1, it is impossible for the effect to be significant, and in this case “ns,” for “not significant,” is substituted for p. If the F statistic is greater than 1 and p is greater than .05, the result does not meet the acceptable threshold for significance and p is reported as p > .05

### 6.1.2 More than two test conditions