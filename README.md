Homework6 Report

2020/7/18



一、已完成的工作：

1. 阅读论文

   DeepInf框架解决的是根据活跃邻居用户分析预测用户是否活跃，是否具有影响力的问题。
   主要考虑有3个或以上活跃邻居的用户，这些用户占比仅为8.75%。

2. 复现模型。

   调整参数，完成DeepInf_gcn和DeepInf_gat两个模型的复现。两个模型的代码已上传到github的DeepInf_xuetang文件夹。
   
   参数调整细节工作：所有参数都调整为与论文一致，Lr修改为0.1；instances for training, validation and test分别修改为75, 12.5, 12.5，batch size改为1024。
   
   框架复现细节工作：复现gat代码时，将gcn的train.py原代码中model的default参数修改为gat即可运行。
   
   
   
二、对比：

1. 实现的结果与论文结果的对比：

   原代码运行performance不高，GCN框架的F1值仅为48.35。参考论文调整参数后，GCN框架的F1值提高到了53.21，提高了4.86个百分点。
   
   GAT框架方面，未修改参数时，框架的F1值为52.18。参考论文调整参数后，F1值提高到了59.27，提高了7.09个百分点。
   
   论文中设计的参数基本为框架内最优的参数。

2. GCN与GAT的对比
   
   GAT相比GCN，performance提高了6.06个百分点。GAT图注意力层与GCN的图卷积层相比，多了一个自适应的边权重系数的维度，可以对其进行自适应力的学习，并通过运用注意力机制，避免引入过多的噪声学习参数，这使得GAT具有高效的表达能力，所以，performance大大提高。
   


三、改进工作

   改进工作可以通过参数调整和模型调整或其他方法来进行。

1. 参数调整层面
   
   本片论文中的参数已经是框架中的最优。还可以通过autoML自动调参对参数进行调优，由于水平和时间关系，这项没能完成。一般来说，论文所涉及的框架在参数层面已经经过调优，performance基本上已经很优秀，通过调整参数带来的performance改进空间不大。如果需要有较大程度的提高，需要从模型本身的设计与修正出发。

2. 其他学者设计的可参考的新框架

   北京邮电大学杨成老师在2019年主要设计的FOREST框架，由于加入了宏观元素，模型的performance有部分提高。由于时间因素，本次作业没有来得及复现。论文名称为：“Multi-scale Information Diffusion Prediction with Reinforced Recurrent Networks”，详见参考资料。

   此外，唐杰老师在近期为“认知推理：从图表示学习和与图神经网络的最新理论看AI的未来”的主题演讲中，对相关主题论述时也提到，一个名为Mixhop的框架对此也有改进。

   R-GCN框架基于GCN基于聚合邻居的操作，又增加了聚合关系的维度，使节点的聚合变成一个双重聚合的过程，是异构图建模，相对于同构图建模的GCN、GAT，表现更佳。由于时间关系也未实现，以后有时间再学习研究。

3. 进一步思考

   从发现潜在影响力用户的角度来说，除了从邻居、关系的图结构挖掘信息，还可以考虑两个方面：

   一是从用户影响力成长时间序列结构的角度来思考，比如纳入用户在不同年度的转发数量的增长变化情况等。这里，有Connecting the Dots框架，值得参考。论文为：“Connecting the Dots: Multivariate Time Series Forecasting with Graph Neural Networks”，详见参考资料。

   二是从节点属性图角度考虑，也可以考虑建立用户个人知识图谱，从概念成色、逻辑思维等进行影响力潜力赋分，发现潜在影响力者。等等。
   
   由于工程能力和建模能力有限，以及时间因素，这些思考尚未实现为model框架，有待于在以后的学习中，继续努力，改进加强。

以上是针对homework6所做的工作和思考，非常感谢老师的审阅，由于时间和水平有限，其中多有错误疏漏、词不达意之处，请老师多多帮助指正，再次感谢：）



四、参考资料：

1. @inproceedings{qiu2018deepinf, title = {DeepInf: Social Influence Prediction with Deep Learning}, author={Qiu, Jiezhong and Tang, Jian and Ma, Hao and Dong, Yuxiao and Wang, Kuansan and Tang, Jie}, booktitle={Proceedings of the 24th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining (KDD’18)}, year={2018}}

2. @inproceedings{ijcai2019-560, title = {Multi-scale Information Diffusion Prediction with Reinforced Recurrent Networks}, author = {Yang, Cheng and Tang, Jian and Sun, Maosong and Cui, Ganqu and Liu, Zhiyuan}, booktitle = {Proceedings of the Twenty-Eighth International Joint Conference on Artificial Intelligence, {IJCAI-19}}, publisher = {International Joint Conferences on Artificial Intelligence Organization}, pages = {4033--4039}, year = {2019}, month = {7}, doi = {10.24963/ijcai.2019/560}}

3. “Connecting the Dots: Multivariate Time Series Forecasting with Graph Neural Networks，作者：Zonghan Wu, Shirui Pan, Guodong Long, Jing Jiang, Xiaojun Chang, Chengqi Zhang，来源：Machine Learning     ，Accepted by KDD 2020，Submitted on 24 May 2020”

4. Relational Graph Attention Networks Dan Busbridge, Dane Sherburn, Pietro Cavallo & Nils Y. Hammerla Babylon Health 60 Sloane Avenue SW3 3DD London, United Kingdom {dan.busbridge, dane.sherburn, pietro.cavallo nils.hammerla}@babylonhealth.com

5. “认知推理：从图表示学习和与图神经网络的最新理论看AI的未来”，作者：学术君，学术头条。2020.4
