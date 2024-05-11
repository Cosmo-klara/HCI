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

为完整起见，让我们来研究第二个例子，即图 6.2b 中的模拟。图 6.6 显示了数据和相应的带有误差条的柱形图。

![ ](./img/29.png)

如前所述，第二次模拟的结果在统计意义上并不显著。图 6.6b 中的大误差条就说明了这一点。方差分析以较高的 P 统计量值显示并证实了结果的不显著性。从图 6.7 中的 P 值可以看出，均值差异有 45% 的可能只是偶然结果。尽管平均值与第一次模拟相同，但参与者的表现差异很大，因此测试条件之间的平均值差异可能只是偶然造成的。例如，观察图 6.6a，8 号学员使用方法 A 在 1.2 秒内完成了任务，而 10 号学员则用了 6.6 秒。很明显，有一些情况超出了两种交互方法的解释能力。

![ ](./img/30.png)

在研究论文中，不显著的结果也需要报告。图 6.8 是第二个模拟的示例。请记住，非显著方差分析并不意味着零假设成立（即均值无差异）。不显著的方差分析只是表明证据不足以拒绝零假设： 零假设仍然成立。

![ ](./img/31.png)

对于不显著的结果，方差分析结果有两种报告方式。如果 F 小于 1，则效应不可能显著，此时用 "ns "代替 p，表示 "不显著"。

### 6.1.2 More than two test conditions

上例中的一个因子有两个水平（测试条件）。实际上，一个因子往往有两个以上的水平。虽然想法相似，但还是值得举例说明。图 6.9 给出了一个假定实验的数据和柱状图，该实验比较了四种用户界面或交互方法。数据是对因变量的观察和测量结果。

![ ](./img/32.png)

对数据进行方差分析，得出图 6.10 所示的表格。首先，我们可以看到 p 小于 0.05，这是公认的显著性临界值。简单地说，测试条件对因变量有显著影响（F3,45 = 4.95，p < .005）。括号中的相关统计数据与之前一样，均来自表格。本例中的自由度有所不同。如果 n 是测试条件的数量，m 是参与者的数量，那么测试条件引起的方差的自由度为 (n - 1)，测试条件 × 受试者引起的方差的自由度为 (n - 1)(m - 1)。

![ ](./img/33.png)

由于方差分析表中的 P 值为 0.0047，因此均值差异是偶然结果的概率小于 0.5%。这种差异很可能是由一种或多种测试条件的固有特性造成的。换句话说，测试条件对因变量的影响在统计学上是显著的。

###  6.1.3 Post hoc comparisons

图 6.10 中的方差分析仅表明，至少有一个均值与至少另一个均值存在显著差异。快速浏览图 6.9b 中的条形图，我们不禁要问，哪些测试条件与哪些其他测试条件不同。要确定这一点，需要进行事后比较检验。图 6.11 中的 Scheffé 检验就是一个例子。在四个测试条件中，可以进行六项比较。其中，只有 A-C 和 B-C 的比较是显著的。换句话说，测试条件 A 和 C 之间以及测试条件 B 和 C 之间的平均值有显著差异。

![ ](./img/34.png)

使用 Scheffé 事后分析的人机交互研究论文包括以下几篇： Chen 和 Chien，2005 年；Czerwinski 等人，1999 年；Fang、Chai 和 Ferreira，2009 年；Freeman、Norris 和 Hyland，2006 年；Kurihara、Vronay 和 Igarashi，2005 年；Kuzuoka、Kosaka 等人，2004 年。

### 6.1.4 Between-subjects designs

上述示例假定采用的是受试者内设计：每位受试者在所有测试条件（因子水平）下接受测试。虽然主体内设计在人机交互中最为常见，但主体间设计也有使用。在对任一设计的数据进行方差分析时，都必须正确设置分析，因为受试者内数据与受试者间数据的方差划分是不同的。

让我们以实验为例，看看左撇子和右撇子用户在使用手写笔添加 PDA 上的日历条目时的差异。根据屏幕布局的不同，左撇子用户在与显示屏右侧的部件交互时可能会发生遮挡。遮挡是否会影响性能？可能会。也可能不会。实验招募了 16 名参与者。手型是一个主体间因素，分为两个层次：左撇子和右撇子，前者有 8 名参与者，后者有 8 名不同的参与者。每位参与者都重复了几次 "添加日历条目 "任务。每位参与者完成任务的平均时间见图 6.12a。虽然研究论文中一般不提供此类表格，但此处提供的数据是为了说明主体间方差分析的组织方式。大多数方差分析应用程序都是在数据矩阵上运行的，矩阵的行数等于参与者的人数，因此图 6.12a 中的数据分为 16 行。 受试者之间的因子被标识为一列增加的名义数据。"L "和 "R "分别代表左撇子和右撇子。

![ ](./img/35.png)

图 6.12b 汇总了按手性分类的结果，而图 6.12c 则以条形图的形式展示了相同的信息，这可能会出现在研究论文中。 对图 6.12a 右两列的 16 × 2 矩阵进行方差分析。结果如图 6.13 所示。自由度分别为：(n - 1)为手感引起的方差，(m - n)为残差引起的方差。

![ ](./img/36.png)

由于图 6.13 中的 P 值大于 0.05，因此左撇子和右撇子之间的差异在统计上并不显著。尽管各组之间的差异约为 10%--左撇子为 22.0 秒，右撇子为 19.9 秒--但观察结果中仍存在相当大的差异。根据这一实验结果，我们认为零假设成立，并得出结论：左撇子和右撇子用户在被测系统上执行添加日历输入任务时没有性能差异。

### 6.1.5 Two-way analysis of variance

有两个自变量或两个因素的实验称为 "双向设计"。对于这类实验，方差分析要测试每个因素对因变量的主效应以及交互效应。显着的交互效应意味着各因素的组合影响或作用于因变量。让我们看看双向方差分析是如何揭示这些效应的。

如果一个实验有两个因素，那么为参与者分配条件就有三种可能。可能是两个因素都在受试者内部分配，也可能是两个因素都在受试者之间分配，还可能是一个因素在受试者内部分配，另一个因素在受试者之间分配。图 6.14 给出了一个假设实验的结果，两个因素都在被试内分配。这两个因素分别是设备和任务，前者有三个水平，后者有两个水平。例如，设备可以是鼠标、轨迹球和手写笔，而任务可以是点选和拖选。但这在这里并不重要。在本示例中，每位参与者都在一个简单的目标捕捉任务中接受了三种设备和两种任务的测试。在这种情况下，实验被称为 "3 × 2 被试内设计"。我们还假定，施测条件的顺序也以某种方式进行了平衡（见第 5 章第 5.11 节）。数据显示的是因变量 "任务完成时间 "的测量反应，单位为秒。

![ ](./img/37.png)

在图 6.14a 中，数据按参与者、设备和任务列出。显然，12 号学员使用设备 3 在 9 秒内完成了任务 2。最下面几行显示的是平均值和标准偏差，是 12 名参与者在每个设备-任务条件下的计算结果。图 6.14b 重新组织了数据，以更清楚地显示设备和任务的效果。如图所示，设备 3 速度最快，设备 1 速度最慢。任务 2 的执行速度略快于任务 1。图 6.14c 以条形图的形式显示了每个设备和任务的平均得分，这可能会出现在研究论文中。误差条显示平均值的 ±1 个标准差。

虽然三种设备和两种任务之间存在差异，但如图 6.14a 底行所示，反应也存在差异。因此，问题仍然是：观察到的差异是否显著，是否可归因于设备或任务的固有特性，或者这些差异只是偶然的结果？这个问题可以通过方差分析来回答。方差分析在图 6.14a 中的 12 × 6 核心矩阵上进行。在准备分析数据时，正确分配因子和水平非常重要。如图 6.14a 所示，列按设备排序，任务嵌套在设备中。结果如图 6.15 所示。

图 6.15 中有三个结果：设备主效应、任务主效应和设备与任务交互效应。让我们看看如何将这些结果从方差分析表中提取出来，并在研究论文中呈现。图 6.16 给出了一个例子。

![ ](./img/38.png)

在介绍统计结果时如何激发读者的兴趣是一项挑战。如果读者面对的是一个又一个乏味无趣的统计数字，他很快就会失去兴趣。报告结果的目的就是从实验研究中出现的大量数据中，有选择性地抽取出有趣的、有启发性的测量和统计结果。请注意图 6.16 中的表述，如 "差异不大"、"稍快 "和 "完全由于"。这些都是为了提高结果的可读性而做的小修饰。需要进一步讨论来解释结果（例如，"设备 3 在任务 2 中的性能提高归功于...."）。

当然，重要的是数据，而不是统计数据。统计检验有助于评估假设，但它们本身并不是结果。Day 和 Gastel（2006, 63）进一步强调了这一点："一般来说，对统计方法的冗长描述表明作者最近才获得这些信息，并认为读者也需要类似的启迪"。不要觉得必须解释方差分析或任何其他统计方法。根据数据给出结果，并简单明了地传达辅助统计检验，无需赘述

### 6.1.6 ANOVA tool

本书网站上有一个名为 Anova2 的 Java 工具。Anova2 是一个命令行应用程序，可以处理文本文件中的数据，并在控制台上生成一个方差分析表。该工具支持五种设计：

+ 单向，有一个被试内因子

+ 单向，带一个被试间因子

+ 具有两个被试内因子的双向设计

+ 带一个主体内因子和一个主体间因子的双向设计

+ 具有两个主体内因子和一个主体间因子的三向分析

为了说明 Anova2 的一般操作，图 6.17 显示了不带参数运行程序时的使用信息。

![ ](./img/39.png)

虽然应用程序接口提供了大量说明和示例，但这里只包含一个示例。文件 dix-example-10×2.txt 包含图 6.18 所示的数据。数据来自 Dix 等人（2004, 337）描述的图标识别假定实验。单因子 (F1) 是图标设计，分为自然和抽象两个层次。数据是任务完成时间（因变量）的测量值。第一列是自然图标的任务完成时间，第二列是抽象图标的任务完成时间。每行包含一名参与者的测量结果。假设实验有 10 名参与者

![ ](./img/40.png)

自然图标的平均任务完成时间（未显示）为 697.7 秒，抽象图标的平均任务完成时间为 750.3 秒。显然，自然图标的识别时间比抽象图标少 7.0%。通过方差分析可以确定这种差异是否具有统计学意义，或者是否可能是偶然造成的。该分析由命令行启动，并向控制台输出方差分析表。(见图 6.19）。

从表中可以看出，研究论文中可能会写道："实验表明，图标类型对任务完成时间有显著影响（F1,9 = 33.36，p < .0005）。

### 6.1.7 Counterbalancing and testing for a group effect

如前一章所述，如果在被试内分配一个因子，则必须抵消不同条件下的学习效果。最常见的方法是平衡。对于有两个水平（A 和 B）的单因素，这就需要把参与者分成两个相等的组。一组（G1）先测试 A，再测试 B；另一组（G2）先测试 B，再测试 A。这样做的目的是平衡或抵消任何学习效果。如果平衡起作用了，就不应该有群体效应，即 G1 和 G2 之间没有显著差异。很简单，但如何知道平衡起作用了呢？研究群体效应的方法是将群体视为主体间因素。当然，小组并不是研究课题意义上的因素。尽管如此，仍可将组作为被试间因子来组织数据，并通过方差分析来检验组效应--组对因变量的主效应。

我将通过修改上一节中的图标设计示例来说明这一点。由于设计是在被试内进行的，我们假定使用了平衡来抵消学习效应。10 名参与者分为两组，每组 5 人。一组先测试自然图标，然后测试抽象图标（NA）。另一组的测试条件顺序正好相反（AN）。修改后的数据如图 6.20 所示。受试者之间的组别标识符作为一列单独的名义数据出现。还添加了标题行。这是 Anova2 的可选功能，用于提高方差分析表的可读性。

![ ](./img/41.png)

为了进行方差分析，现在的实验是一个 2 × 2 设计，包含一个对象内因子（图标类型，包含自然和抽象两个水平）和一个对象间因子（组别，包含 NA 和 AN 两个水平）。使用 Anova2 对图 6.20 中的数据进行方差分析，使用相同的命令，只是指定了新文件，注意到存在两个水平的被试间因子，并包含表示存在标题行的 -h 选项。(见图 6.21。）从顶行可以看出，群体效应并不显著（F1,8 = 0.466，ns）。这是一个好消息。组间效应不显著意味着平衡起到了作用。任何可能发生的学习都被平衡掉了。尽管由于在计算方差时对数据进行了新的分区，F 值和 p 值略有不同，但实验的主要结果保持不变。结果仍然是图标类型对任务完成时间有显著影响（F1,8 = 30.68，p < .0005）。

![ ](./img/42.png)

图 6.21 中还有第三个效应。这是图标类型和组别之间的双向交互效应。从方差分析表中可以看出，该效应不显著（F1,8 = 0.277，ns）。如果该效应显著，则表示存在一种称为非对称技能转移的现象（Poulton，1974 年），即存在学习效应，而且从 A 过渡到 N 与从 N 过渡到 A 是不同的（见第 5 章第 5.12 节）。

在许多研究实验中，都会对受试者内部因素进行平衡，而不对群体效应进行实际测试。这在很大程度上是一种选择。有关方差分析的一些练习示例，请参阅本章末的学生练习。

##  6.2 Chi-square test

研究各种关系的常用统计程序是卡方检验，也称皮尔逊卡方检验，有时用 "平方 "代替 "方"。其发音为 kī（与 sky 押韵）。分类变量或名义变量之间的关系代表了人、交互方法、系统等的属性。数据通常以或然率表的形式进行汇总--或然率表是一种交叉表，将数据按行和列组织起来，每个单元格都包含该类别中观察结果数量的计数或频率数据。千方检验将观察值（表中的计数）与预期值进行比较。预期值是在假设表中类别之间没有差异的前提下得出的。卡方检验是一种非参数检验，因为类别是名义尺度属性，没有相关的概率分布。一个假设的例子可以说明这一点。

考虑开展一项研究项目，调查男性或女性在使用台式电脑系统时滚动的方法是否有所不同。为了研究这个问题，我们对大量用户进行了观察。对于每个用户，我们都会记录下他们是男性还是女性，以及他们是使用鼠标滚轮 (MW)、通过点击和拖动滚动条 (CD) 还是键盘 (KB) 进行滚动。分类为性别（男、女）和滚动方式（MW、CD、KB）。图 6.22a 以 2 × 3 或然率表的形式提供了数据。共观察到 1001 位用户，包括 56 位男性和 45 位女性。使用滚动方式的人数分别为 49 人（MW）、24 人（CD）和 28 人（KB）。图 6.22b 以条形图的形式显示了数据，这可能会出现在研究论文中。

![ ](./img/43.png)

浏览一下数据和图表就会发现，男性和女性在台式电脑上滚动的方法可能确实存在差异。只有 9 位女性使用点击和拖动，而男性则有 15 位。不过，总体上观察到的男性更多，因此差异并没有想象中那么大。那么，问题在于观察到的差异是真实存在的，还是仅仅是随机效应造成的。为了确定这一点，我们使用了卡方检验。检验统计量用希腊文小写字母 chi 表示，写作 χ2。与方差分析一样，检验的基本假设是 "无差异"，目的是拒绝该假设。但与方差分析不同的是，卡方检验非常简单。使用电子表格应用程序就可以轻松完成计算。让我们来详细了解一下这个例子。

卡方检验是观察值与期望值之间的比较，期望值考虑了不同的行列总数。图 6.23a 显示了图 6.22a 中数据在无差异假设下的期望值。每个预期值都是行总计乘以列总计，再除以总计。例如，男性-兆瓦预期值为 (56 × 49) / 101 = 27.2。如图 6.23b 所示，根据观察值和预期值，创建一个卡方表。每个卡方是（观测值减去预期值）除以预期值的平方。例如，男性-女性的卡方为 (28.0 - 27.2)2 / 27.2 = 0.025。

最终的卡方值是表中各个卡方的总和。对于示例数据，结果为 χ2 = 1.462，如图 6.23b 中右下角单元格所示。要确定单元格条目之间是否存在统计意义上的显著差异，需要将最终的卡方与临界值表中的值进行比较。如果卡方超过临界值，则或然表中的差异具有统计意义，这意味着表中的名义量纲变量存在显著差异。还需要两个细节：(a) 自由度，(b) 显著性所需的α 值或 p 值。卡方统计的自由度为 (r - 1)(c - 1)，其中 r 是行数，c 是列数。在本例中，df = (2 - 1) (3 - 1) = 2。α水平在测试前选定。本例使用 α = .05。显著性临界值可在表格中查找。在 α = .05 和 df = 2 时，临界值为 χ2 = 5.99。由于计算值 χ2 = 1.462 小于临界值，观察值的差异（见图 6.22）在统计上并不显著。因此，我们得出结论，男性和女性使用台式计算机系统的滚动方式没有差异。

![ ](./img/44.png)

为方便起见，本书网站提供了一个 ChiSquare Java 工具。它可以处理包含数据表的文本文件，数据表的行和列包含或然表中的计数。除了自动计算奇平方统计量 χ2 外，该实用程序还计算并输出概率 p，因此无需使用查找表。图 6.25 显示了实用程序对包含图 6.22a 中数据的文本文件的处理过程。

让我们再看一个例子，在这个例子中，结果具有统计学意义，并使用事后比较检验来确定哪些条件之间存在显著差异。

A researcher wishes to investigate whether students, professors, and parents agree in their responses to a question about mobile phone usage during classroom lectures. To study this, a large number of students, professors, and parents are randomly sampled and asked if they agree that students should be allowed to use mobile phones during classroom lectures. The categories are Opinion (agree, disagree) and Person (student, professor, parent). In all, 300 people were sampled, including 40 students, 60 professors, and 200 parents. The responses were: 120 agree and 180 disagree. The contingency table in Figure 6.26 shows the data organized by Opinion and Person. Evidently, respondents overall feel that the use of mobile phones during classroom lectures should not be allowed. Furthermore, the responses are in the same direction for all three categories of people. However, a closer look at the table reveals some variation among the categories. Although three times more students disagreed than agreed, only a few more parents disagreed than agreed. To determine if the differences in response are statistically significant, a chi-square test is used.

![ ](./img/45.png)

The calculations leading to the chi-square statistic are identical to those demonstrated for the last example. The result in this case is χ2 = 20.5 with df = 2. With reference to Figure 6.24, the chi-square statistic exceeds the critical value both for α = .05 (5.99) and for α = .001 (13.82). Clearly, there is a difference in opinions among students, professors, and parents on the question of interest. However, since there were three categories of people, a post hoc pairwise comparisons test is required to determine which categories differ from one another. The ChiSquare utility on this book’s website includes a −ph option to perform the post hoc comparisons. (See Figure 6.27.) The comparisons indicate statistical significance (p < .05) for the 1:3 and 2:3 comparisons. Thus, on the question at issue there is a differ
ence in opinion between students and parents and between professors and parents. However, there is no difference in opinion between students and professors.

Finally, let’s consider an example using data from a paper published in the ACM SIGCHI conference proceedings. Ayyavu and Jensen researched tools to assist users in determining if websites are considered trustworthy (free of spam, predators, etc.) (Ayyavu and Jensen, 2011). In particular, they were interested in differences in the ratings provided by community-based tools versus heuristics-based tools. They examined Web Of Trust (WOT) as a community-based tool and McAfee’s Site Advisor (MSA) as a heuristics-based tool. The tools were presented with 20,000 websites and for each site the tools provided an assessment of good (safe), bad (not safe), or unsure. After removing sites for which WOT or MSA gave an unsure rating, 18,650 remained. Ayyavu and Jensen presented the results for these sites in a contingency table, formatted as shown in Figure 6.28. Thankfully, most of the sites were deemed good, or safe. WOT rated 9.21 percent of the sites bad, or not safe. The figure was 3.36 percent for MSA. That seems like a substantial difference. To determine if the difference was statistically significant, a chi-square test was used. The result was χ2 = 543.5 with df = 1. That’s well above the critical value of χ2 = 3.84 for p < .05 (see Figure 6.24). Ayyavu and Jensen concluded that there was a statistically significant difference between the assessments provided by the tools. In fact, they reported that the difference was “highly significant,” noting that the chi-square statistic exceeded the p < .0001 critical value (Ayyavu and Jensen, 2011, p. 2309).

![ ](./img/46.png)

A contingency table combined with a chi-square test is a simple and effective way to study relationships in HCI research. The relationships are frequently between attributes of people (males versus females, Mac users versus PC users, etc.) and their behaviors (e.g., preferred scrolling method, texting habits, etc.). But as the last example illustrates, the attributes may also involve systems and the behaviors of systems. A few additional examples of chi-square tests in the HCI literature are as follows: Bartneck, Verbunt, Mubin, and Mahmud, 2007; Kane, Wobbrock, and Ladner, 2011; Kindberg et al., 2008; Qvarfordt, Jönsson, and Dahlbäck, 2003). See also student exercises 6-6 to 6-8 at the end of this chapter.

## 6.3 Non-parametric tests for ordinal data

Non-parametric tests make no assumptions about the probability distribution of the population from which the underlying data are obtained. For this reason, non- parametric tests are applicable to a wider range of data than parametric tests. However, there is a downside to non-parametric tests: loss of information. While parametric tests such as the analysis of variance operate on interval or ratio data, most non-parametric tests deal with ordinal data (ranks). Non-parametric tests ignore any property of the scale of data except ordinality. If the data tested are in fact interval or ratio, non-parametric tests waste this knowledge by collapsing differences into ranks. For example, a trio of values such as 49, 81, 82 (perhaps student marks on an exam) is transformed to 1, 2, 3. Clearly information is sacrificed, since the middle value is now equidistant from the first and third. Non-parametric tests benefit by not being bound by parametric assumptions, but sacrifice the power to use all available information to reject a false null hypothesis.

In the examples ahead, non-parametric tests are described as they are typically used in HCI research—to analyze ordinal (and sometimes interval) data. The data are typically obtained through questionnaires (e.g., using a Likert scale), preference ratings, or assessments on a scale. Rather than using direct measurement of human responses, the data are obtained subjectively, from participants, or using heuristics or other non-empirical or semi-empirical methods.

The four most common non-parametric procedures are the Mann-Whitney U test, the Wilcoxon Signed-Rank test, the Kruskal-Wallis test, and the Friedman test. Each is used in a particular context, depending on the number of test conditions and the experiment design. (Figure 6.29 illustrates.) Between-subjects and within-subjects designs generate data that are from independent samples and correlated samples, respectively, as shown in the figure. Between-subjects designs generate independent samples because different participants are tested with each condition. Within-subjects designs generate correlated samples because the same participants are tested with each condition. Bear in mind that the conditions are levels of a single independent variable (factor) in the experiment.

![ ](./img/47.png)

The non-parametric tests in Figure 6.29 are demonstrated below through a series of hypothetical examples. As the problems are described and the data presented, it will be apparent which test is appropriate. Since the Kruskal-Wallis and Friedman tests operate on three or more conditions, a statistically significant outcome is usually followed with a post hoc pairwise comparisons test. This is also demonstrated. For each example, two versions of the data analysis are provided. One uses StatView (now JMP), a commercial statistics application. The other uses a Java utility provided on this book’s website. The results are identical for both analyses. Let’s begin.

###  6.3.1 Example 1

A researcher seeks to determine if there is a difference in the political leanings of Mac users versus PC users. Are Mac or PC users more likely to have political views leaning to the left or to the right? The experimenter randomly selects 10 Mac users and 10 PC users.15 The participants are interviewed and asked a variety of questions about their political views. Each participant is assessed on a 10-point linear scale (1 = very left, 10 = very right) with the results stored in a file as a table with 10 rows and two columns. The first column contains the assessments for the Mac users, the second column for the PC users. The data are given in Figure 6.30

![ ](./img/48.png)

The mean score for the Mac users is 3.7 and for the PC users 4.5 (not shown). Evidently, the PC users are a little more “right-leaning.” But is the difference real or is it just an artifact of the variability in responses? The data are potentially intervalscale, but the researcher senses that the intervals between successive codes are not equal, because they are based on a qualitative assessment. The data are at least ordinal, so a non-parametric test is chosen to answer this question. There are two conditions and the assignment is between-subjects, therefore the appropriate test is Mann-Whitney U (see Figure 6.29). The results are shown in Figure 6.31a using StatView (now JMP) and in Figure 6.31b using the MannWhitneyU Java utility from the book‘s website. There are numerous behind-the-scenes data manipulations and calculations leading to the test statistic, U. The output also includes a normalized z-score (calculated from U) and p, the probability of obtaining the observed data under the null hypothesis of “no difference”. Two z and p values are provided. The second set includes a “correction for ties.” In most cases, the difference with the corrected values is minor.

![ ](./img/49.png)

For the example, U = 31.0 with p = .1418 (corrected for ties). Since p is greater than .05, the differences in the assessments have not met the customary threshold for statistical significance. The conclusion for the hypothetical experiment is that there is no difference in the political leanings of Mac users and PC users (U = 31.0, p > .05)

### 6.3.2 Example 2

A researcher is interested in comparing two new designs for media players. There is a particular interest in knowing if the designs differ in “cool appeal” for young users. Ten young tech-savvy participants are recruited and given demos of the two media players  (MPA, MPB). The participants are asked to rate the designs for cool appeal on a 10-point linear scale (1 = not cool at all, 10 = really cool). The data are given in Figure 6.32.

![ ](./img/50.png)

The mean rating for media player A is 6.4 and for media player B 3.7 (not shown). It seems media player A fares quite well compared to media player B. However, there was some variability in the responses, so perhaps the difference was just a chance outcome. To test if the differences in the ratings are real, a statistical test is used. Since the data are interval-scale (see discussion for Example 1), a nonparametric test is chosen. There are two test conditions and the design is withinsubjects, therefore the Wilcoxon Signed-Rank test is appropriate (see Figure 6.29).

The results are shown in Figure 6.33a using StatView and in Figure 6.33b using the WilcoxonSignedRank Java utility available on this book’s website. The test statistic for the Wilcoxon Signed-Rank test is a normalized z score. For the example, z = −2.254 with p = .0242 (corrected for ties). Since p is less than .05, the customary threshold for statistical significance is exceeded. The conclusion is that the two media players differ in “cool appeal” (z = −2.254, p < .05)

![ ](./img/51.png)

### 6.3.3 Example 3

The designers of a new GPS system for automobiles are wondering if age will be a factor in the acceptance of the product. They decide to conduct a small experiment to find out. Eight participants are recruited from each of three age groups: 20–29 years, 30–39 years, and 40–49 years. The participants are given a demo of the new GPS system and then asked if they liked it enough to consider purchasing it for personal use. They respond on a 10-point linear scale (1= definitely no, 10 = definitely yes). The data are given in Figure 6.34.

![ ](./img/52.png)

The mean scores by age group are 7.1 (20–29), 4.0 (30–39), and 2.9 (40–49) (not shown). It seems there is a difference, since the 20–29 year age group gave higher acceptability scores than the other two groups. However, there was also some variability in the scores. So the question remains: are the differences in the acceptability scores among the three age groups statistically significant, or are the differences simply a chance outcome? Since the data are interval-scale (see discussion for Example 1), a non-parametric test is chosen to help answer the question. There are three age groups and the design is between-subjects, therefore the Kruskal-Wallis test is appropriate (see Figure 6.29). The results are shown in Figure 6.35a using StatView and in Figure 6.35b using the KruskalWallis Java utility available on this book’s website

![ ](./img/53.png)

The test statistic is H, which follows a chi-square distribution with df = k − 1 (k is the number of groups). In the example, H = 9.605 with p = .0082 (corrected for ties). Since p is below the customary threshold for statistical significance (.05), the test shows a significant effect of age group on the acceptability of the GPS design (χ2 = 9.605, p < .01, df = 2).

There are three age groups, therefore a post hoc pairwise comparisons test is needed to determine which age groups are significantly different from one another. This is available in the Java utility using the −ph option.17 (See Figure 6.36.) As is evident, the only statistically significant pairwise comparison was between pairs 1 and 3; that is, between the 20–29 year group and the 40–49 year group

![ ](./img/54.png)

###  6.3.4 Example 4

A researcher has implemented four variations of a search engine interface (A, B, C, and D). Each interface uses a different dialogue for users to build their queries. The researcher wishes to know if the interfaces differ in the quality of results they produce. Eight participants are recruited and are given a demonstration of each interface and then asked to do a series of search tasks. The “quality of results” is assessed for each participant and for each search engine. The assessment uses a linear scale from 1 to 100 (1 = very poor, 100 = very good). A Latin square was used to balance the order of conditions, but this isn’t important here. The data are given in Figure 6.37.

![ ](./img/55.png)

The mean scores for the search engines from A to D were 71.0, 68.1, 60.9, and 69.8 (not shown). The spread is only about 10 points between the highest and lowest assessments, so it unclear if there is any difference in the quality of results between the four interfaces. Nevertheless, it is worthwhile testing for significant differences. Since the data are interval-scale (see discussion for Example 1), a nonparametric test is chosen to investigate further. There are four test conditions and the conditions were assigned within-subjects, therefore the Friedman test is appropriate (see Figure 6.29). The results are shown in Figure 6.38a using StatView and in Figure 6.38b using the Friedman Java utility available on this book’s website. 

![ ](./img/56.png)

The Friedman test statistic is H, which follows the chi-square distribution with n − 1 degrees of freedom (n = number of conditions). As seen in the figure, there is indeed a difference in the quality of results between the four search engine interfaces (χ2 = 8.692, p < .05, df = 3). A post hoc pairwise comparisons test is needed to determine which search engine interfaces are significantly different from one another. This is available using the −ph option of the Friedman Java utility.(See Figure 6.39.) With four conditions, there are six pairwise comparisons. Only two were significant: 1:3 and 3:4; that is, between interfaces C and A, and between interfaces C and D.

![ ](./img/57.png)

###  6.3.5 Discussion

In the examples above, the data were summarized using the means (averages) for each condition. This is common in HCI research for data of this sort. It is also valid. Since the assessment scales were described as “linear,” the data are interval-scale.

Therefore, the mean is the correct statistic for central tendency. However, many HCI experiments use questionnaires with response items presented on a Likertscale or some other combination of numbers and verbal tags. Since the response items are subject to human interpretation, the data may not be interval-scale in the strictest sense (cf. temperature). If the scales are non-linear, then the quality of the data is compromised. In the worst case, the data degrade to ordinal and the appropriate statistic for central tendency is the median (middle value) or mode (most common value). In some research papers, questionnaire responses are summarized using the mean, while in other papers the median is used. On this subject we enter a grey area, with researchers holding different opinions on which measure is the correct measure. Some claim outright that Likert-scale responses are ordinal and that it is simply wrong to report means (e.g., Robertson, 2012). The truth is likely somewhere in the middle (i.e., between interval and ordinal).

The non-parametric tests demonstrated above are limited to single-factor analyses. The Friedman test, for example, can analyze many conditions, but the conditions are all levels of a single factor. The test cannot be used for multi-factor analyses, such as a 2 × 3 design or a 4 × 2 × 2 design. (Of course, the parametric ANOVA is applicable to multi-factor experiments.) Although there are extensions of non-parametric tests to multi-factor experiments (Kaptein et al., 2010; Wobbrock, Findlater, Gergle, and Higgins, 2011), the value of these tools to HCI research is limited. Non-parametric tests are most commonly used to analyze questionnaire data or ratings, as in the examples above. Questionnaires are rarely administered for each condition in a multi-factor experiment (e.g., 4 × 2 × 2 = 16 times). Typically, a single questionnaire is used when testing is finished, with the goal of gathering participants’ comments and preference ratings on the conditions tested (perhaps in a multi-factor experiment). In this case, the non-parametric tests demonstrated above are fine. One possible exception is the use of non-parametric tests for ratio-scale data, which I discuss in the next section.

## 6.4 Parametric versus non-parametric tests

When alternative tests are available to study data in an experiment, a rationale is needed to choose among the possibilities. For statistical tests, the guiding principle is that of power. Statistical power is about improving the odds of getting it right with the null hypothesis: rejecting the null hypothesis when it should be rejected and not rejecting it when there is no (or insufficient) basis to do so. However, there are other issues to consider. Siegel (1957) suggests that an appropriate test is one where the measurement requirements of the test are consistent with the measurements used in the research. Of the four scales of measurement—nominal, ordinal, interval, ratio (see section 4.1.4 in chapter 4)—the pairings are simple. If the research data are ordinal, then a statistical test that operates on ordinal data is a good choice. Similarly, if the experimental data are ratio, then a statistical test that operates on ratio data is a good choice. In HCI, there is a common (and perhaps growing) practice that cuts across this simple principle. In this final section on hypothesis testing in HCI research, we venture into territory that was declared off-limits in this chapter’s introduction: controversy. The incursion will be brief, however.

Parametric tests, such as the analysis of variance, assume the data are sampled from a probability distribution, such as the normal distribution. Provided this assumption is met (and a few others are), parametric tests have more statistical power and are more accurate and more precise than non-parametric tests. However, if the assumptions are not met, then the researcher must decide on the appropriate course of action. There are three possibilities: (1) proceed with the parametric test, (2) transform or clean the data in some manner to correct the violations and then proceed with the parametric test, or (3) use a non-parametric test. All three options have advantages and disadvantages. Proceeding with a parametric test on data that potentially violate underlying assumptions is a common approach. This may occur because researchers don’t understand or don’t have access to statistical tools that test the assumptions. Also, some researchers feel parametric tests are reasonably robust to violations and, in any event, the underlying assumptions are rarely met when analyzing real data (Erceg-Hurn and Mirosevich, 2008). Researchers with a particular concern for violations in assumptions are likely to choose one of the  latter two options. However, both come at a cost. Transforming data using a log or power function is an effective way to correct the violations in assumptions. But as Siegel asks, “Will the process of ‘normalizing’ the distribution by altering the numerical values of the scores cause a distortion in the experimental effect under investigation?” (Siegel, 1957, p. 14). He notes that this is a question the investigator may not be able to answer. Sheskin adds, “One might view a data transformation as little more than a convenient mechanism for ‘cooking’ data until it allows a researcher to achieve a specific goal,” while allowing “When used judiciously, data transformation can be a valuable tool” (Sheskin, 2011, p. 483). So the issues in transforming data are a matter for deeper consideration. The third option, which seems to be increasingly common in HCI research, is to proceed with  a non-parametric test. Conveniently, this approach sidesteps questions about the probability distribution of the underlying data. However, the decision to use a nonparametric test on data that are potentially parametric but violate assumptions is not to be entered into lightly. Let’s consider this point further.

For ordinal data, such as rankings or qualitative assessments on a scale, nonparametric tests are the logical choice. For ratio data, such as measurements of human performance, parametric tests are preferred, in part due to their increased power (the ability to reject a false null hypothesis) but also by the simple standard that the test-to-data pairing is correct. But do ratio-scale human performance measurements meet the requirements for parametric data? Put another way, are measurements such as the time or errors in completing tasks normally distributed? The answer to this question is never yes in a precise way. The data are samples and therefore inherit a multitude of haphazard, even capricious, tendencies. If the samples are expected to bring forth precise properties of a probability distribution, such as normality, then disappointment looms. There are numerous tests for normality, skewness, etc., and small sets of empirically sampled data will frequently fail. If the data are measures on a dependent variable collected in an experiment, a researcher may conclude that the data are not parametric and then proceed with a non-parametric test. But this may be unnecessary or unwise. Recall from our earlier discussions that non-parametric tests collapse data into ranks. As Sheskin notes, “When a researcher elects to transform a set of interval/ratio data into ranks, information is sacrificed” (Sheskin, 2011, p. 531). So choosing a non-parametric test for ratio-scale measurements that deviate from normality is to replace one deficiency with another. Restraint is advised. The procedures and instrumentation put in place to collect ratio-scale human performance data in experimental research should not be muted so casually, as occurs if the data are downgraded to ordinal (ranks).  Let’s examine a few related points.

In the 1950s and early 1960s, applied statistics in the social sciences experienced a broad migration to non-parametric tests. However, abandoning parametric tests—mainly the parametric ANOVA—in favor of non-parametric tests was largely unnecessary, as noted by Glass et al. (1972). The shift occurred because researchers asked the wrong question. They asked “Are the assumptions of the parametric ANOVA met?” instead of “What are the consequences of the inevitable violations in the parametric ANOVA?” The first of these two questions is easy to answer, as there are numerous “assumption tests” for parametric data. However, the second question presents formidable challenges. For one, standards of rigor necessarily degrade when a researcher moves from studying a mathematical model under defined assumptions to studying that same model under violations to the assumptions. Examining the consequences of violations in assumptions requires empirical data, which are deviate, or simulated data, which are deviate by design. It’s a difficult and highly complex assignment. But all is not lost. Considerable research into these issues exists (although not in HCI). In the end, there is evidence that the parametric ANOVA is reasonably robust to violations in the underlying assumptions. Even with small sample sizes (e.g., n = 3), the consequences of violations in the assumptions underpinning the ANOVA are usually minor. Let’s have a look at the use of non-parametric tests on ratio-scale data in HCI research.

Non-parametric tests, such as the Mann-Whitney U, Wilcoxon Signed-Rank, Kruskal-Wallis, and Friedman tests, are well-travelled in the HCI literature. In most cases the tests are used with questionnaire data and the like. That’s appropriate since the data are ordinal (or perhaps interval). Yet there are examples where a non-parametric test was used on ratio data that were obtained experimentally. This 
use of non-parametric tests merits additional scrutiny. To investigate this, a small meta-analysis was undertaken using a sample of 25 publications from the HCI literature. (See Figure 6.40.) What we find in studying these examples may provide insight into this application of non-parametric tests in HCI research

![ ](./img/58.png)

Each example publication in Figure 6.40 presents the methodology and results of an HCI experiment or user study. In each case, the effect of an independent variable on a dependent variable was tested using a non-parametric procedure. The dependent variables were ratio-scale performance measurements, so a parametric test could have been used. The dependent variables included the following: task completion time (Ali, Scholer, Thom, and Wu, 2009; Gajos et al., 2008; Hayashi, Pendleton, Ozenc, and Hong, 2012; Huhtala, Karukka, Salminaa, and Häkkilä, 2011; Jacko  et al., 2004; Kuzuoka, Yamazaki, et al., 2004; J. Liu et al., 2010; Perugini, Anderson, and Moroney, 2007; Stanton, Kahn Jr., Severson, Ruckert, and Gill, 2008; Wilson, Brewster, Halvey, Crossan, and Stewart, 2011; Xiao et al., 2009), accuracy or errors (Banovic et al., 2011; Elmqvist, Henry, Riche, and Fekete, 2008; Findlater et al., 2010; Hinckley, Baudisch, Ramos, and Guimbretière, 2005; Kane, Bigham, and Wobbrock, 2008; Seager and Fraser, 2007; Wilson et al., 2011), distance (Caniard and Fleming, 2007; Rantanen, Verho, Lekkala, Tuisku, and Surakka, 2012), signal strength (Solovey et al., 2012), and counts such as number of clicks (Farzam et al., 2008), number of search sources (J. Liu et al., 2010), number of disorientations (Seager and Fraser, 2007), number of collisions (Solovey et al., 2012), number of objects dropped (García, Molina, Gonzalez, Martínez, and Martínez, 2009), and number of elements drawn (Sylla, Branco, Coutinho, and Coquet, 2009). Why were non-parametric tests used? In some cases, no rationale was given (Banovic et al., 2011; Elmqvist et al., 2008; Findlater et al., 2010; Hayashi et al., 2012; Hinckley et al., 2005; Kane et al., 2008; Kuzuoka, Yamazaki, et al., 2004; Rantanen et al., 2012; Stanton et al., 2008; Wobbrock et al., 2009). In other cases, the researchers expressed concern over violations in the assumptions of the parametric ANOVA. The following is a sample of the explanations leading to the choice of a non-parametric test: “The time data is not normally distributed” (Ali et al., 2009, p. 303), “The distributions are skewed” (Caniard and Fleming, 2007, p. 103), “[The] Shapiro-Wilk W test for non-normality suggests that the sample is unlikely to be from a normal distribution” (Farzam et al., 2008, p. 565), “[The data] did not meet the requirements for normality (Kolmogorov-Smirnov test)” (García et al., 2009, p. 260), “The distribution of task completion times was significantly different from a normal distribution” (Perugini et al., 2007, p. 968), and “The data did not fit a normal distribution” (Wilson et al., 2011, p. 150). In none of the papers cited did the researchers articulate concern forthe loss of information in using a non-parametric test on ratio data. In eschewing the parametric test, these researchers were evidently concerned with the first of the two questions noted earlier: are the assumptions of the parametric ANOVA met? Of the 25 examples, only two went the extra distance to consider the second question: what are the consequences of the violations? Munteanu et al. reported

>  Although we tested the data for normalcy, a non-parametric (distribution-free) test, Friedman’s Rank Test for correlated samples, was also run and chi-square scores were computed, in order to confirm the validity of the F-scores obtained through ANOVA 

(Munteanu, Baecker, Penn, Toms, and James, 2006, p. 497)

The results of both the parametric and non-parametric tests were given. As it turns out, the tests lead to the same conclusion. Perugini et al. reported:

> Since the distribution of task completion times was significantly different from a normal distribution, we also used the Mann-Whitney U test for non-parametric statistical significance. However, since the patterns of significant differences (p < .05) of the eight tasks were the same for the ANOVA and the Mann-WhitneyU, we present the results for the ANOVA” 

(Perugini et al., 2007, p. 968)

In both of these examples we see a hint of caution—that there is an issue around the use of a non-parametric test versus a parametric test. So which test is the correct test? At this juncture, it would be remiss to recommend strict testing of ratio data using a parametric test (despite violations in assumptions) or a non-parametric test (despite loss of information). Arguably, the balance tips in favor of parametric tests due to the added precision and statistical power. However, the practice of Munteanu et al. (2006) and Perugini et al. (2007) is laudable: examine both avenues, consider the outcome for each, and attune for possible contradictions