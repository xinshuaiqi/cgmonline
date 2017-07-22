---
title: 自制简单遗传算法实验
date: '2013-09-15T10:36:35+00:00'
author: 何通
categories:
  - 优化与模拟
tags:
  - 旅行商问题
  - 最优化
  - 进化
  - 遗传算法
  - 随机搜索
slug: manual-genetic-algorithm
forum_id: 418969
---

我参加完八月份的COS沙龙之后比较闲，忽然想起自己很久以前看的遗传算法的基本思想。本着时不时就应该做一些私活的心态，我就在旅行商问题上面把它实现了一下。

# 遗传算法

遗传算法是一个仿生学的算法。进化论认为地球上千奇百怪的生物都是进化而来的，如今能生存在地球上的生物是更适应于这个环境的，我们也可以说它们是被“优化过”的。他们是怎么优化的呢？在一个种群中，生物的差异主要来自于两点，不同染色体之间的交叉结合以及染色体自发的随机变异。这些差异实际上是随机发生的，但是生物的外部生存环境会通过生存与死亡让更能适应的个体存活下去。因此随着时间的推移，生物种群对环境的适应能力会越来越高。受到这个现象的启发，有人发明了遗传算法，通过模拟遗传的过程来解决一些优化问题。<!--more-->
 
我们假设需要解决的问题空间类似于地球生物圈，问题的一个可能解也就被类比成一条有多个基因的染色体。作为简化，我们认为一条染色体就代表了一个生物，另一方面，你也可以理解为生物进化的胜利实质上也是染色体的进化胜利。首先我们要有初始的生命种子，即一些随机的染色体，然后我们对这些染色体定义“繁殖”、“突变”和“死亡”的概念，就能够让它们在这个空间里自由发展。“繁殖”指的是两条染色体之间产生相互而变化，生成新的染色体的过程；“突变”指的是每条染色体都可能以微小的概率改变自己的基因的过程；“死亡”就是把某条染色体从种群中移除，也就是被淘汰了。那么我们怎么衡量每一条染色体是不是比它的小伙伴活得更自在呢？我们可以针对具体的环境，定义一个适应度函数，用来评估每个染色体对这个环境的适应程度，然后以这个适应程度为权重决定它们是否能活到下一代。下表是生物和算法中的概念关系的总结：

* 问题的一个解↔染色体
* 问题的背景↔生物圈环境
* 解的适应度↔染色体在这个环境下的生存几率
* 构成解的基本单元↔基因
* 解和解之间的基本单元交换↔繁殖
* 单个解自己的基本单元变化↔突变
* 不再考虑某个解↔死亡

因为孕育了生命的地球一直以来都没有变成火星，也没有变成金星，是一个相对固定的环境。遗传算法在此基础上发展而来，它也不是什么问题都适用的，而是需要在一个相对固定的环境里面进行发展。如果我们每一步的决策会改变当前的局势（比如下棋这样和对手交互的游戏），那么我认为这时遗传算法不是最合适的，顶多只能够用在其中一个子问题当中。比如R的skmeans算法就有遗传算法在每一步迭代中优化的版本。

有一些问题的大环境是不变的，我们可以在上面利用遗传算法求解。对于某一个特定的迷宫，我们可以认为每次往哪个方向前进是构成解的基本单元，这些基本单元连在一起就成为了一个解，借助据此行动之后离出口的曼哈顿距离还可以定义适应度。又比如在一个n维空间内部搜索某个确切函数的最大值时，我们可以将每一维的坐标作为基本单元，某个点就是一条n个基本单元构成的解，这个点的函数值便是适应度。除去这些比较老旧的话题，我们还有更好玩的例子，就是[让一群自行车在地图上面跑](http://boxcar2d.com/)，希望得到在这个地图上跑得最远的（还有[多辆车同时竞赛的版本](http://gencar.co/)）。在这个例子中，自行车的轮胎数量、大小以及其中的连接结构分别是一个解的不同基本单元，它们能够构成一个自行车，适应度函数则是程序模拟过后的最大行驶距离。

除了这些例子，[这里](http://userweb.eng.gla.ac.uk/yun.li/ga_demo/)还是一个学院派的在线演示样例，需要Java支持。

这些东西好玩，但是对于我这么鶸的码力而言，一个周末很可能连基本的环境都搭建不好。所以我选择了几乎不需要搭建环境的旅行商问题。

# 旅行商问题

某个国家有N个城市，有一个商人希望能在每一个城市推销他的产品，所以他希望能够从某个城市开始，把每个城市都走一遍，最后再回到一开始的地方。可是这个国家的路费十分昂贵，所以他希望这么一趟下来走的总路程最短。这个优化的问题就是旅行商问题。

旅行商问题是一个经典的NP问题，所以除了枚举求解全局最优之外，人们只能通过近似算法来求较优解。这些近似算法中，就包括了遗传算法。其实人们已经对这个问题的遗传算法有过不少研究，[这里](http://www.dca.fee.unicamp.br/~gomide/courses/EA072/artigos/Genetic_Algorithm_TSPR_eview_Larranaga_1999.pdf)是一篇较早的比较性论文，里面带有几个数据的实验，不过这是我写了代码之后才看到的，也就并没有实现上面所有的算法，希望对此有更系统了解的读者可以参考一下。

下面是我的算法细节策略，这个策略的每个部分都有着改进的过程。

# 评分与淘汰

通常来讲，我们会给这一代种群的每个染色体赋予一个值，然后以这个值为权重作为染色体的存活概率。因为旅行商问题希望得到越小越好的连线，因此我们应该认为距离反比于每条染色体的存活率。我一开始粗糙地求出这个地图的一个上界，然后让存活率正比于每个染色体的距离与这个上界的差。后来发现以一个常数作为上界太粗糙了，应该与时俱进，所以我将这个上界改了一下，定义为当前种群中最长距离加一的值。

我假设整个族群的个体数量是偶数，然后每次以存活概率进行抽样，只留下一半的种群用以繁殖出另一半。

# 繁殖

繁殖的方案有很多种选择，我这里的方案是自己随意定下来的，没有经过严格而仔细的比较，并不能保证是最优的。

在淘汰部分所述的假设前提下，我们有一半的族群来繁殖另一半。首先我将所有存活的染色体复制一份，然后让它们随机与原染色体进行繁殖。

对于两条云雨过后的染色体a和b，我一开始是这样定义它们的子代的：数量m代表繁殖中可能会变化的基因数量，随机选择a的m个位置，将这些位置上面的基因按照b中的顺序排列后放回。但是实际上这个问题里的相邻基因之间有着非常密切的关系，这样的查找实际上只是一个随机搜索罢了，不能起到很快收敛到更优排列的作用。

于是我改进了子代的定义：数量m仍然代表繁殖中可能会变化的基因数量，不过我先随机选择a的一个位置，将这个位置开始之后的m个连续基因按照b中的顺序排列后放回，即造成一段连续的变化。这样这个方法就更有“目的性”，更容易对一个局部区域找到更好的连接方式。

# 变异

对于每条染色体，我希望每次至多只有一个基因会产生变异，这个基因是这样选出来的：事先设定一个概率p，然后生成长度等于染色体基因数的均匀分布随机数列，挑出所有小于概率p的基因（如果有的话），再在它们当中选择一个即可。选出这个基因之后，我再挑出另一个基因并交换它们。这并没有很好地照顾基因前后之间的关联性，所以我改进了一下变异的方法：我挑出另一个基因之后，将之前选出要变异的基因插入到这个位置上，就像往链表中加入元素一样。

# 跳出局部最优

在实验中发现，到了后期算法开始无法突破瓶颈，可能需要很多次的迭代才能得到一个微小的进步。这种情况也许是算法效率上的问题，也许是陷入了一个难以再大踏步进化的局部最优中。为了从这样的情况下跳出来，我尝试了许多的算法，这里就不赘述了，直接说一下我最后改进到的算法。

为了跳出局部最优，我选择了“灭绝”的方法，就是在一定的条件下将最厉害的精英杀死。如果超过了一定的步骤N，当前的族群仍然固步自封，我就将最好的一个或几个染色体杀死，用族群内部的次好染色体代替他们，并继续进化下去。但是这样单纯地杀死精英有点浪费，所以我选择将被灭绝的精英储存起来。当我储存够了K个精英时，就将它们全都释放出来，在几匹不同意义的好马同时出现时就有可能催生出一匹强力的超级小马。经过实验，效率最高的应该是K=2。每次释放精英我都称作一个“时代”。这里“一定的步骤”N也是随着时代增加而不断增加的。

# 实验结果

如果使用完全随机的地图，旅行商问题是很难通过人眼看出**“这种方案离最优解的差距还有多远”**的。所以我在单位圆上等间距地生成了100个点，以此作为地图，这样便能通过人眼来比较当前方案的优劣程度。

下面的动态图就是在这个地图上应用遗传算法的全程进化过程展示。可以看出，一开始的一万代能够很快地从一个随机的情况进化到一个较好的结果，之后效率则会有明显的下降了，而最后的几次进化则花费了非常久的时间。

![GA2](http://ww3.sinaimg.cn/mw690/61830650jw1e84jucph1dg20fk0gob2b.gif)

最后，[代码](https://github.com/hetong007/code4cos/tree/master/Genetic%20Algorithm%20for%20Travelling%20Salesman%20Problem)在这里，仅供参考，欢迎捉虫。