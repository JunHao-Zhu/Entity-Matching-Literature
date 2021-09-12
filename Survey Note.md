# **关系型数据-知识图谱协同关联方法研究--Survey**	



## **Relational Data**

### **End-to-End Task Based Parallelization for Entity Resolution on Dynamic Data**

*Leonardo Gazzarri, Melanie Herschel*    **ICDE 2021** (Citations: **0**)

**Motivation:**

考虑了两种**动态**的数据库的实体解析：1）增量式（有限数量实体的周期更新）2）流动式实体更新。需要一个速度快、精准的实体解析算法，希望将blocking和ER两个环节**并行处理** 

**Contributions:**

* 提出针对动态数据的端到端框架
* 将ER pipline定义为了一个个function的串联
* 对block和ER两个环节进行并行处理，特别是将block cleaning和comparison clean进行修改，使其更适合平行化。

### **Rotom: A Meta-Learned Data Augmentation Framework for Entity Matching, Data Cleaning, Text Classification, and Beyond**

*Zhengjie Miao, Yuliang Li, Xiaolan Wang*    **SIGMOD 2021** (Citations: **0**) 

**Motivation:**

深度学习方法需要大量的高质量数据进行训练，因此现有的工作在预训练模型的基础上再通过部分高质量的训练集fine tune模型，这样的方式取得了不错的效果。但这这样的方式也需要大量的高质量数据集，但获取高质量的训练集是一个开销很大的工作。

**Challenges of Data Augmentation for EM:**

* DA技术可能反而会破坏样本，例如导致样本的label变化等问题污染训练集
* 找到最优的DA算子或者规则并不简单，这些算子常常会引入超参

**Contributions:**

* 适用于多任务。将多种任务看作sequence classification，通过预训练语言模型处理sequence classification
* InvDA 利用seq2seq进行数据扩充
* 通过meta learning的方式调整过滤/加权模型**自动优化扩充的数据**

**Idea:**

可以将Meta Learning用到知识图谱的数据扩充上，利用Meta Learning修改知识图谱的attribute或者连边结构，产生一个新的连边。

### **Dual-Objective Fine-Tuning of BERT for Entity Matching**

*Ralph Peeters, Christian Bizer*    **VLDB 2021** (Citation: **0**)

**Motivation:**

在实际中的数据集成设定中，我们能够获取部分实体的标识符（例如GTIN、ORCID等）而部分却无法得到。在这样的设定下，将存在标识符的数据作为训练集，然后去训练并不存在标识符的数据是有一定困难的。

**Contribution:**

Dual-Objective实现两种目标：商品种类的分类任务（多分类任务）和match/no match的二分类任务。这样的模型更适合于上述的应用场景（在数据多的情况多分类任务部分更好的work，数据少的情况下二分类任务部分更work）。

**Weaknesses:**

因为JointBERT是针对multi-classes情况，如果测试数据中出现OOD数据，那么JointBERT的效果大打折扣。另外，对于训练数据较少的情况下，他的效果不如其他的EM模型

### **Automating Entity Matching Model Development**

*Pei Wang, Weiling Zheng, Jiannan Wang, Jian Pei*    **ICDE 2021** (Citations: **0**)

**Motivation:**

尝试将Auto-ML技术应用到EM任务中

**Contribution：**

* 将Auto-ML技术应用到了EM任务中，自动选择机器学习模型进行Entity Matching
* 通过自训练的方式学习更多标签，获得更多的数据

**Weaknesses:**

1. Auto-ML还只是对Matching这个部分进行的，能不能够将blocking也加入到automating这部分
2. Auto-ML在一定的时间内找到一个最优的模型，但这个模型不一定是全局最优的。Auto-ML的搜索空间太大

### **Online Topic-Aware Entity Resolution Over Incomplete Data Streams**

  *Weilong Ren, Xiang Lian, Kambiz Ghazinour*    **SIGMOD 2021** (Citations: **0**)

  **Motivation:**

  考虑提取的实体的attribute存在缺失以及数据动态输入的情况

  **Contribution:**

  设计一个**Topic-Aware**的模型，除了考虑两个实体之间的attribute之间是否相似外，还考虑了两个实体之间的Topic是否相近。

  **Weakness:**

  Topic-Aware只是去看attribute中是否包含了某一topic的关键词，这个关键词是人为给出的，不够全面。

  **Inspiration:**

  对于数据库和知识图谱的对齐，是否考量实体的topic的相关度，如果两个实体对应的topic是一致的，那么这两个实体就是对齐的，可以进行融合。

### **GNEM: A Generic One-to-Set Neural Entity Matching Framework**

  *Runjin Chen, Yanyan Shen, Dongxiang Zhang*    **WWW 2021** (Citations: **0**)

  **Motivation:**

  如果表中的两个记录指向同一个实体，那么表中与这两个记录相似的其他记录有很大可能也指向的是这一实体，反之亦然。已知的实体关系能够帮助去预测未知的记录之间的关系。

  **Contributions:**

  * 提出了**Generic One-to-Set neural framework (GNEM)**，构建matching pair graph将表中的记录转变成一个Graph。利用图中现有记录的配对情况帮助实体解析
  * GNEM也可以作为现有其他EM模型的扩展，有很强的通用性

**Weaknesses:**

有监督训练，需要的label数据；用$V_r$构建的网络训练的GCN仅仅适用于$V_r$，对于另外的就要重新训练

  **Inspiration:**

  将表格中的记录数据转变成了Graph数据（对记录对作为Graph的节点，做一个节点分类），knowledge graph也可变成matching pair graph

### **Cost-effective Variational Active Entity Resolution**

  *Alex Bogatu, Norman W. Paton, Mark Douthwaite, Stuart Davie, Andre Freitas*    **ICDE 2021**

**Motivation:**

现有ER模型需要大量的labeled data以及大量的训练时间，这项工作将VAEs应用到ER任务中，将feature engineering和similarity进行解耦

**Contribution:**

* 对实体进行映射的时候，不需要大量的有标签数据学习到一个比较好的嵌入向量，在映射这部分实现无监督

**Weaknesses:**

用VAE生成嵌入向量的效果应该没有BERT这种pre-trained model好，没有考虑context信息等

### **Improving the Efficiency and Effectiveness  for BERT-based Entity Resolution**

*Bing Li, Yukai Miao, Yaoshu Wang, Yifang Sun, Wei Wang*    **AAAI 2021** (Citations: **2**) 

**Motivation:**

ER suffers from quadratic pairs of co-references, which is of high time complexity.

**Contributions:**

* blocking和matching步骤都变成BERT-based

**Weaknesses:**

1. 需要大量标签数据对模型进行训练；
2. blocking所需要的时间复杂度挺高的，高于大部分blocking
3. blocking需要保证recall率，但这种情况下真的能保证recall接近1吗

### **Deep Entity Matching with Pre-Trained Language Models**

*Yuliang Li, Jinfeng Li, AnHai Doan, Wang-Chiew Tan*    **VLDB 2020** (Citations: **34**)

**Motivation:**

1) 若要在大数据集上实现实体匹配，需要对求解空间进行剪枝；2) 若要实现更好的实体匹配需要理解关键语句和一些特定领域的知识

**Contribution:**

* 将EM看作序列对分类问题，提出基于预训练语言模型的DITTO模型（第一个将transformer用到EM问题）
* 通过融合domain knowledge、总结精简长语句并且通过数据扩充增加训练数据提升性能
* SOTA on the benchmark, 在减少label的情况下仍然能够实现很好的效果
* 在实际的大数据集中仍能work并取得很好的效果

**Note**

模型的重点：将数据库中的**数据转换成token sequence**，然后用nlp技术处理。可以不用理会数据库中存储数据属性格式，因为全部变成了类似于自然语言的token sequence。知识图谱存储的数据是异构的，知识图谱也应该可以适用这样的序列化处理。然后做了很多**剪枝**的工作，例如输入额外的一些信息--这些信息帮助剪枝，信息的标准化、长句缩写。

The positive  rate ranges from 9.4% to 25%. 正样本的占比其实很小，训练数据是不平衡的，小样本训练  -> 对抗学习

### **Multi-Context Attention for Entity Matching**

*Dongxiang Zhang, Yuyang Nie, Sai Wu, Yanyan Shen, Kian-Lee Tan*    **WWW 2020** (Citations: **8**)

**Motivation:**

最近对于EM任务的进展大多在应用了机器学习，以DeepMatcher和DeepER为例，他们都仅仅使用了简单的RNNs和注意力机制，EM精度仍存在很大的提升空间。

**Contributions:**

引入self-attention、pair-attention以及global-attention获得更多维度的信息，其次还引入了attribute attention来减少不可信赖的特征带来的副作用

**Weaknesses:**

想法挺简单的，但是效果和同类的supervised方法比起来并不好

### **Efficient Entity Resolution on Heterogeneous Records**

*Yiming Lin, Hongzhi Wang, Jianzhong Li, Hong Gao*    **TKDE 2020** (Citation:**4**)

**Motivations:**

异质的数据库的实体解析任务存在两个问题：

1. 两个schema对同一个实体的描述可以从不同的角度出发，这造成description difference现象
2. 两个schema中对于字面上attribute很有可能指的是一个attribute，但因为对这些信息的缺乏使我们很难直接比较两个attribute

本文尝试解决这两个问题

**Contribution:**

1. 提出了**super record**，能够merge指向相同实体的两条记录形成一个新的记录，包含更多信息，并用比较两条记录的生成的super record的相似度
2. 设计了index来加快HERA的执行

**Weaknesses:**

1. 针对的是Structured类型的数据，不适用于Textual和Dirty类型的数据

### **ZeroER: Entity Resolution using Zero Labeled Examples**

*Renzhi Wu, Sanya Chaba, Saurabh Sawlani, Xu Chu, Saravanan*    **SIGMOD 2020** (Citations: **15**)

**Motivation:**

无监督的方式训练ER模型。通过统计发现，matched和unmatched记录的属性的嵌入向量在分布上相距很远，因此可以利用这一点来建立生成模型获得特征向量训练分类器，从而达到无label训练的效果

**Contribution:**

* **无监督式：** 采用GMM来根据已知的数据生成match和unmatch样本的概率分布，用生成的样本进行模型的训练
* **效果好：** 精度优于其他无监督式的ER方法，相较于state-of-art的监督式ER方法，ZeroER也可以获得相当的效果
* **效率高：** 采用迭代式的极大似然法获得GMM参数去生成样本

### **A Comprehensive Benchmark Framework for Active Learning Methods in Entity Matching**

*Vamsi Meduri, Lucian Popa, Prithviraj Sen, Mohamed Sarwat*    **SIGMOD**

**Motivation:**

**Contribution:**

* 为active learning based EM建立标准的框架
* 通过实验比较了不同active learning方法的EM效果

### **ERGAN: Generative Adversarial Networks for Entity Resolution**

*Jingyu Shao, Qing Wang, Asiri Wijesinghe, Erhard Rahm*    **ICDM 2020** (Citations: )

**Motivation:**

解决EM模型的两个问题：1）过拟合问题；2）label不平衡的问题

**Contribution:**

引入GAN模型解决EM问题：Label Generator和一个Discriminator之间的博弈，除此之外引入了diversity模块和propagation模块分别解决过拟合问题以及label不平衡问题

### **Deep Learning for Entity Matching: A Design Space Exploration**

*Sidharth Mudal, Han Li, Theodoros Rekatsinas, AnHai Doan, Youngchoon Park et al.*    **SIGMOD 2018** (Citations: **245**)

**Motivation:**

将deep learning用到EM任务中，是EM任务中非常经典的论文。首次讨论DL对EM任务有何帮助，在什么样的EM任务上能够取得好的效果，将DL引入EM任务有什么优势以及挑战等问题。

**Contribution:**

* 首次定义了design space，使用了复杂度不同的4种方法来生成嵌入向量
* 对structured EM，textual EM和dirty EM都进行了实验。其中前面两种被广泛地研究，但dirty EM并没有得到很好的关注
* 相比传统的方法，发现DL在Structured data上并没有取得优势，而在textual和dirty数据上DL的优势明显

**Weaknesses:**

论文里面设计的design space如果涉及DL方法就需要大量的labeled data，否则效果并不好。design space对于structured数据效果没有明显的优势。

### **Robust Entity Resolution using Random Graphs**

*Sainyam Galhotra, Donatella Firmani, Barna Saha, Divesh Srivastava*    **SIGMOD** [(PDF)]() (Citations: **16**)

### **Distributed Representations of Tuples for Entity Resolution**

*Muhammad Ebraheem, Saravanan Thirumuruganathan, Shafiq Joty, Mourad Ouzzani, Nan Tang*  **VLDB 2018** (Citations: **140**)

## **Knowledge Graph** [[To Relational Data](#Relational Data)]

### **Entity Alignment for Knowledge Graphs with Multi-order Convolutional Networks**

*Nguyen Thanh Tam, Huynh Thanh Trung, Hongzhi Yin, Tong Van Vinh et al.*    **ICDE 2021** (Citations: **0**) 

**Motivation:**

此前的生成嵌入的方法嵌入了大量的无关信息。entity embedding一方面需要将语法信息编码，另一方面编码语义信息。现有的模型没有很好地利用实体的特征信息。

**Contribution:**

* 提出了统一的、**无监督的**、**自适应的**实体对齐模型，**适用于跨语言的知识图谱**
* 对于**跨语言的知识图谱**的实体一致满足：1.实体一致性；2.关系一致性；3.属性一致性，此模型同时满足3个性质

**Weaknesses:**

计算复杂度。看代码感觉是一个整个图full batch训练，有点类似于VGAE，复杂度可能会有点高

### **Visual Pivoting for (Unsupervised) Entity Alignment**

*Fangyu Liu, Muhao Chen, Dan Roth, Nigel Collier*    **AAAI 2021** (Citations: **1**)

**Motivation:**

现有的问题：entity alignment的训练集没有足够的标签，KG的稀疏性导致结构关联性比较弱。

不管哪种语言或者哪种模式的KG，**视觉信息**对于指定的实体来说是比较**普适**的；在KG中image信息容易获得并且质量高，视觉信息更容易**扩充数据**。

**Contributions：**

* 首次在entity alignment中**使用images信息**
* 使用**图像相似性**来代替标签信息，实现**无监督学习**
* 通过消融实验给出各个模态的可解释性

**Weaknesses:**

虽然取得了很好的效果，但其实要求很高，因此会包含图像信息的知识图谱并不多，局限性比较大

### **Make It Easy: An Effective End-to-End Entity Alignment Framework**

  *Congcong Ge, Xiaoze Liu, Lu Chen, Baihua Zheng, Yunjun Gao*    **SIGIR 2021** 

  **Motivation:**

  两个主要的提升空间：1. Labor-intensive preprocessing；2. 语义信息的使用不充分

  **Contribution:**

  * 灵活的EA框架：end-to-end，无需人为的预处理
  * 轻量化：通过NEAP先做了一个blocking的处理，减少对象数量
  * 可信的EA

**Weaknesses:**

1. 空间复杂度是$n^2$ （不止$n^2$，仅仅考虑entity matching matrix就有这个复杂度了）
2. Entity similarity matrix的好坏还是由structured-based EA module决定，模型对一些超参会比较敏感，比如相似度的阈值等等超参。

### **Boosting the Speed of Entity Alignment 10$\times$: Dual Attention Matching Network with Normalized Hard Sample Mining**

*Xin Mao, Wenting Wang, Yuanbin Wu, Man Lan*    **WWW 2021** (Citations: **0**)

**Motivation:**

现有的EA方法具有很大的时间复杂性，对于比较大的数据集需要很长的时间运行才能得到结果。现有算法的复杂性来源于 1. 过于复杂的图编码器；2. 不够有效的负采样策略。

**Contribution:**

1. 降低模型复杂度，仅对Cross KG和inner KG两部分模型获得的信息；
2. 提出了Normalized Hard Sample Mining Loss来解决现有随机采样信息量少以及Truncated Uniform Negative Sampling strategy效率低的问题；

### **Relation-Aware Neighborhood Matching Model for Entity Alignment**

*Yao Zhu, Hongzhi Liu, Zhonghai Wu, Yingpeng Du*    **AAAI 2021** (Citations: **1**)

**Motivation:**

现有的一些方法仅仅聚合节点上的信息，但同时也会将噪声聚合。现有的研究也没有关注到entity之间的relation信息，relation alignment和entity alignment之间具有正向的关系。

**Contribution:**

* 在一个框架中实现relation alignment和entity alignment，两个任务相互增强
* 使用语义信息

**Weaknesses:**

实际使用时，distance matrix是iteration迭代出来的，算法效率存疑

### **Business Entity Matching with Siamese Graph Convolutional Networks**

*Evgeny Krivosheev, Mattia Atzeni, Katsiaryna Mirylenka, Paolo Scotton, Christoph Miksovic, Anton Zorin*    **AAAI 2021** (CItations: **0**)

这篇感觉没啥意思

### **Collective Multi-type Entity Alignment Between Knowledge Graphs**

*Qi Zhu, Hao Wei, Bunyamin Sisman, Da Zheng, Christos Faloutsos, Xin Luna Dong, Jiawei Han*    **WWW 2020** (Citations:**9**)

**Motivation:**

知识图谱中存在大量不同类型的实体，以及这些实体之间的关系往往不同，甚至实体之间存在多重关系，一般GNNs不能满足这些特性。而且因为知识图谱不一定完整，因此两个相同的实体在不同的知识图谱之中的连接关系很可能不同，如果直接使用GNNs往往因为连边不同导致精度下降。

**Contributions:**

* **cross-graph attention**关注两个知识图谱中的相似邻居，**relation-aware self-attention**避免随意地匹配有相同邻居的两个实体
* 能够适应大规模知识图谱的实体对齐

**Weaknesses:**

将fastText编码后的向量放入GNN中反而破坏fasttext生成的编码后的向量。
