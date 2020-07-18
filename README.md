Homework6 Report

2020/7/18

一、已完成的工作：
1. 阅读论文
   DeepInf框架解决的是根据邻居用户分析预测用户是否具有影响力的问题。

2. 复现模型。
   调整参数，完成DeepInf_gcn和DeepInf_gat两个模型的复现。两个模型的代码已上传到github的DeepInf_xuetang文件夹。
* 参数调整细节：
所有参数都调整为与论文一致，除了batch size保留为原框架的2048。
Lr修改为0.1；instances for training, validation and test分别修改为75, 12.5, 12.5。

* 框架复现细节
复现gat代码时，将gcn的train.py原代码中model参数修改为gat即可运行。即如：“parser.add_argument('--model', type=str, default='gat’, help="models used")”
   

二、对比：
1. 实现的结果与论文结果的对比：
   原框架运行performance不高，GCN的F1值为48.35。参考论文调整参数后，GCN的F1值提高到了53.49，相比论文GCN的F1值53.21，提高了。
   GAT方面，未修改参数时，框架的F1值为52.18，参数调整跟论文设置参数一致时，F1值提高到了58.32，与论文结果一致。

2. GCN与GAT的对比
    GAT相比GCN，performance提高了5个百分点。GAT图注意力层与GCN的图卷积层相比，多了一个自适应的边权重系数的维度，可以对其进行自适应力的学习，并通过运用注意力机制，避免引入过多的噪声学习参数，这使得GAT具有高效的表达能力，所以，performance大大提高。

三、改进工作
改进工作可以通过参数调整和模型调整或其他方法来进行。
1. 参数调整层面
保留了batch size 2048的设置，performance有所提高。
通过automl自动调参也可以对参数进行调优。不过一般来说，论文框架里实现的performance一般参数层面已经经过调优，通过调整参数带来的performance改进空间不大，如果需要有较大程度的提高，需要从模型本身的修正出发。
2. 据了解，北京邮电大学杨成老师在2019年主要设计的FOREST框架，由于加入了宏观……元素，performance有所提高。论文名称为：github地址为：FOREST框架，由于时间因素，没有来得及复现。
此外，唐老师也提到，Mixhop框架也有改进。
据了解，R-GCN框架基于GCN基于聚合邻居的操作，又增加了聚合关系的维度，使节点的聚合变成一个双重聚合的过程，是异构图建模，相对于同构图建模的GCN、GAT，表现更佳。由于时间关系，无法实现，以后有时间再学习研究。
3. 从发现潜在影响力用户的角度来说，除了从邻居、关系的图结构挖掘信息，还可以考虑两个方面：
一是从用户影响力成长时间序列结构的角度来思考，比如纳入用户在不同年度的转发数量的增长变化情况等。这里，有Connecting the Dots框架，值得参考。论文为：“Connecting the Dots: Multivariate Time Series Forecasting with Graph Neural Networks，作者：Zonghan Wu, Shirui Pan, Guodong Long, Jing Jiang, Xiaojun Chang, Chengqi Zhang，来源：Machine Learning     ，Accepted by KDD 2020，Submitted on 24 May 2020”。
二是从节点属性图角度考虑，也可以考虑建立用户个人知识图谱，从概念成色、逻辑思维等进行影响力潜力赋分，发现潜在影响力者。等等。

以上是针对homework6所做的工作和思考，非常感谢老师的审阅，由于时间和水平有限，请老师多多帮助指正，感谢。


参考资料：
1. @inproceedings{qiu2018deepinf, title={DeepInf: Social Influence Prediction with Deep Learning}, author={Qiu, Jiezhong and Tang, Jian and Ma, Hao and Dong, Yuxiao and Wang, Kuansan and Tang, Jie},
  booktitle={Proceedings of the 24th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining (KDD’18)}, year={2018}}

2. @inproceedings{ijcai2019-560,
  title     = {Multi-scale Information Diffusion Prediction with Reinforced Recurrent Networks},
  author    = {Yang, Cheng and Tang, Jian and Sun, Maosong and Cui, Ganqu and Liu, Zhiyuan},
  booktitle = {Proceedings of the Twenty-Eighth International Joint Conference on
               Artificial Intelligence, {IJCAI-19}},
  publisher = {International Joint Conferences on Artificial Intelligence Organization},             
  pages     = {4033--4039},
  year      = {2019},
  month     = {7},
  doi       = {10.24963/ijcai.2019/560},
  url       = {https://doi.org/10.24963/ijcai.2019/560},
}



3. “Connecting the Dots: Multivariate Time Series Forecasting with Graph Neural Networks，作者：Zonghan Wu, Shirui Pan, Guodong Long, Jing Jiang, Xiaojun Chang, Chengqi Zhang，来源：Machine Learning     ，Accepted by KDD 2020，Submitted on 24 May 2020”。

4. Relational Graph Attention Networks Dan Busbridge, Dane Sherburn, Pietro Cavallo & Nils Y. Hammerla Babylon Health 60 Sloane Avenue SW3 3DD London, United Kingdom {dan.busbridge, dane.sherburn, pietro.cavallo nils.hammerla}@babylonhealth.com
