# DeepInf_xuetang

作业完成事项：
1. 实现gcn：已完成，代码已附；
   实现gat：已完成，代码已附。
2. gcn与gat的对比
   gcn 运行10个半小时；
   
   用windows的jupter会不会快一点，等等看。
   
   jupter，windows gcn 20个小时预估。比mac 终端慢一半。阿里云呢？是慢还是根本就跑不了？
   
   但是似乎jupter，windows gcn比mac跑出来的performance要好不少。
   
   
   
   gat 运行两天。估计，1.74天；估计明天下午一点半跑完。（windows，gcn，jupter，估计明天上午6点跑完）
   
   gat比gcn的perfermance好5%？

3. 改进方面
   杨成的可不可以嫁接过来。他好像有新的数据。
   唐老师是不是提升了可以用别的
   pscn，这个，代码倒是便宜，performance是不是差？

4. 
（1）微博有三个以上互关大V的人是非常少的，这群人也并非转发的主要人群，微博的任务应该是激活那些没有互关大V，或者只有一个互关大V的用户，怎么能够让他们变成有三个互关大V，这对社交传播更加有利。只有大V互转并不能促成社交传播变强。

（2）deepwalk这种随机游走的算法在社交网络里面效率肯定是很低的，肯定会找影响力大，而且距离近的。注意力机制GAT是满足了这两个条件吗？

只要有一个影响力大，距离离他最近的，原本影响力大，但是离他远，或者离他近，但是影响力小的强得多。

还有一个潜在的好处是，如何识别潜在影响力强，比如只有5000粉丝，但是只要有一个机遇，就变成100万粉丝的大V，如果是企业家，或者爆款作品的演员，爆款paper的学者，即将。这样的传播增长效率高

（3）

一、研究的是什么问题？
V1，V2，哪个是活跃用户。
是左边有很多闭合关系的大V的v1，还是右边有很多开放关系的大V的V2？
谁的影响力更大？

在这里，衡量影响力大指标是什么：转发多？

影响力最大的用户，不是那种有多少大V互相关注的用户，虽然互关，但有可能不转发，是死用户，付出多少努力的用户。愿意在微博上经营且个人能力有潜力的用户。
统计的转发量不是粉丝量吗？input的是啥？

类似的有，图书编辑要发现谁最有潜力写书，是阅读数还是转发数，还是内容完整性、体系性

很多特征提炼不起来。

有个人为什么让我，是因为有人转发

搜索的作用没有提到。有的人被转发，是因为搜索，主题、不是因为关注。
