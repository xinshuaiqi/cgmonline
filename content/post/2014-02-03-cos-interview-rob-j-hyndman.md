---
title: COS 访谈第十五期：Rob J. Hyndman
date: '2014-02-03T17:40:05+00:00'
author: COS编辑部
categories:
  - 新闻通知
  - 统计之都
  - 职业事业
tags:
  - COS访谈
  - 时间序列
  - 统计分析
slug: cos-interview-rob-j-hyndman
forum_id: 419003
---

【COS编辑部按】：受访者：[Rob J. Hyndman](http://robjhyndman.com/)，采访者：[Earo Wang](http://earo.me/)，译者：[黄俊文](http://www.fyears.org/)。原文[在这](http://earo.me/2014/01/interview-with-rob/)。

Rob J. Hyndman 是澳大利亚的 [Monash University](http://www.monash.edu/) 的统计学教授以及 International Journal of Forecasting 的主编。他也是 `forecast` 和 `hts` 等广泛被使用的 R 包的作者。

**Earo**: 你曾经获得的是理学荣誉学士学位。那么你为什么选择统计学作为你的专业，以及统计学有什么吸引到你的呢？

**Rob**: 最初我在获得理学学位的途中，我没有想过统计学有关的东西，我本来是打算学习数学的。当时，Melbourne University 的数学相关专业的学生都要求在第一年上统计学，数学，计算机科学的课程。所以我就选择了统计学。不过我发现它很有趣，因为我很喜欢使用数学工具来解决现实问题的过程。<!--more-->

在第一年的暑假，我找到了一份 Melbourne University 的 [Statistical Consulting Centre](http://www.scc.ms.unimelb.edu.au/) 的工作，主要是 debugging code。在我找到 bugs 之后，我尝试找个时间对我的老板说明我干了什么，不过他总是很忙。我知道我必须要为我的客户写一个报告，所以最后我就自己写了一份报告并且放到了老板的桌面上。之后，老板打电话给我说“我觉得我应该长期录用你”。在那个夏天末尾，我决定选择统计学专业。下一年，我读大二，我在一个学术会议上发言，内容是关于我的一个咨询项目的，因为客户想我谈谈一个我完成的工作。我在那个咨询工作投入很多，也很享受那个过程。这就是我如何成为一个统计学学家的过程。

**Earo**: 既然你已经做了二十多年的学者，那么你觉得现在的统计学的课程结构等和你本科时代的还是不是一样？

**Rob**: 本科课程很相似。也许它应该改变更加多。（但是怎样变化呢？）我觉得统计学相关训练应该加入更加多的计算，特别是当数据集变得更加大和复杂的时候。当然课程是会变化的，但是大学在本科教育中的变化很慢，特别是开始的几年。另一方面，在任何好的大学，高等的课程都应该不断的更新。

**Earo**: 你提到了在大数据时代我们应该加入更加多的计算的训练。那么你是怎样定义大数据的？以及你认为数据科学和统计学之间的关系是怎样的？

**Rob**: 我会采取某些人的对其的定义：如果问题去计算的时间比起建立其数学模型的时间更加长，那么这就是一个大数据问题。大部分统计分析的工作都是建立模型而不是进行计算，因为计算机运行得很快。但是，如果情形相反，那么肯定是一个有关一个很大的数据集的问题了。另一个大数据的定义是，那些不能塞进你计算机内存的数据集就是大数据。至于数据科学和统计学的关系？我觉得统计学是数据科学的一个子集。数据科学是一个更加大的概念，包含数据管理，数据存储等；与此同时统计学基本上是关于数据集的随机性，怎样分析它和怎样汇报分析结果。不过如何管理大数据集是数据科学的一个很重要的课题，不过它经常被统计学分析所忽视。很多人认为数据科学对于统计学家来说是很时髦和吸引的词汇。不过我倾向于认为数据科学的内涵更加广阔。

**Earo**: 因为数据科学的特性，有很多很多的计算机学家参与到数据科学的领域中。那么统计学家比起计算机学家有什么优势呢？

**Rob**: 比较大的优势是对随机现象的建模的理解。大部分计算机学家没有任何真正的对随机模型的训练，以及他们经常不理解一些比如不确定性的概念和对噪声的处理。在数据科学的问题中，一个常见的任务是从噪声数据中提取信息，统计学家在这里有巨大优势。另一个问题是量化不确定性。典型地，在进行预测的问题中，数据科学家不生成预测区间，只是生成点估计。不过在预测中有着不确定性，以及如果在过程中你有随机成分的话，你可以量化这种不确定性。那就是这一百多年来统计学的总体思想。很多进入数据科学领域的计算机学家没有对不确定性的思维方式。另一方面，他们在其他方面很擅长，比如说算法设计和高效计算。我认为计算机学家和统计学家可以一起工作得很好，因为他们从略微不同的角度去处理问题。我希望数据科学家和统计学家的不同之处最终消失，不过那会是很多年后的事了。

**Earo**: `forecast` 包成为 CRAN 上最常用的 R 包之一了。你能谈一谈你开发这个包的原因吗？

**Rob**: 第一个原因是我有一些用于做咨询工作的函数。我认为把它们集成一个包中是很好的做法。很多人没有好的工具，或者不知道怎样寻找好的工具。我发现我可以使我那些关于预测的函数帮助到很多人，那会很有用。另一个原因是我研究出一些了新的关于预测的方法（模型），我希望大家使用它们，而使大家使用它们的唯一办法是开发软件提供给他们。三十年前，如果你为新的方法或者模型写了一篇论文，并且有人对此感兴趣的话，他们不得不自己实现它们的代码。那时没有共享代码的文化。不过这种情况改变了，如果你对于发展新的统计学模型或者工具，你不得不提供 R 包去让别人实践你的想法。

**Earo**: 你不仅开发 R 包，还是一个博客主人和 [Cross Validated](http://stats.stackexchange.com/) 的活跃用户。你现在是提供在线和公开的教科书的网站 [OTexts](https://www.otexts.org/) 的创始人之一。在我看来，你很活跃于网上的统计学的社区。是什么动力使得你免费做出这些贡献呢？

**Rob**: 我认为，受雇于大学（间接地受雇于澳洲政府）我是需要贡献新的统计学的方法的。对我来说回馈社区是很有意义很值得的。我不明白为什么论文一定要局限于学术期刊。如果你想有所作为，你要公开你的贡献。在公开的环境中做统计研究，同时鼓励公开对话，是非常好的。我认为这样子学科会发展得更加快，信息会更加透明。我有工资收取，所以我不需要额外考虑金钱的来源。我真的不明白为什么有一些学者不愿意开放地进行研究。在民营企业工作的话是很不同的，你要依靠你的研究来维持生活。不过我不需要这样子。

至于为何要写博客呢？因为我想影响人们思考的方式，而且我发现写博客是一个有效的方法。另外因为要回答同样的问题给我的学生和其他人，因此我也用博客来回答他们。我很讨厌重复干一样工作，所以我就在网站上写下我的答案，别人能够看到它们。如果我见到重复的问题，我会写一篇文章。至少，这样会帮助我更加有效地回答问题。我写博客还有一个原因：写博客是一个很好的宣传我的研究工作的方式，我想别人使用我的研究成果。比如说，我也许会写一篇文章，关于多重季节性的估计（multiple seasonality in forecasting）的问题，而且说明了这个问题是怎样用我的 `forecast` 包的一个工具来解决的。没有商业人士会阅读我发表的理论论文，不过他们可能会进行网络搜索，然后发现我的网站上一个例子。，并且运用它。我的工作被更加广泛地使用了，这是一个好现象。我不想写一篇被发表的但从来没有被应用的论文。这些就是我写博客的原因。

至于 Cross Validated 的创立 ，是因为我逐渐收到了很多统计学问题，我觉得如果有个网站能够回答这些问题的话就好了。很多做统计学工作的人没有受到足够的训练去真正理解他们在做的东西。如果他们能够得到一些在线社区的支持的话就会有很多好处。我也关注了给程序员用的 [stackoverflow](http://stackoverflow.com/) ，在这个网站上你可以提出程序的问题，以很快的速度获得非常好的答案。我个人有时也会使用这个网站去解决我的程序的问题，那些问题经常是 R 的问题，不过有时是和我想用的正则表达式有关的。所以我觉得如果有一个统计学版本的这类网站是一件很酷的事情。我向 stackoverflow 公司提出了这个想法，之后我就成为了那个网站的第一个管理员，然后接下来的六个月我把网站事务搞得非常好。我现在还在使用这个网站，不过我已经不是管理员了。

至于教科书，这是一个不同的过程。这要追溯到很久之前。我在 1998 年写了一本关于预测的教科书，这成为了世界上关于统计预测的最畅销的教科书。我的合约方告诉我我应该会得到 5% 的销售分成，不过我实际上获得非常的少。出版商 Wiley 没有除了印刷和营销之外的成本，而且它们对营销很不在行。所以我很不高兴。接着那本书变得过时了。我认为我需要写一个新版本，不过我不想通过 Wiley 来发行它。但是我的合约方说他们有另一个版本的权利，我也不能够写一本和原来版本竞争的新书。经过一段时间的磋商，他们终于允许了我解除那个合约。

经过思考，我发现我写书并不是为了赚钱，我写书的真正目的是因为我想影响大家思考的方式，我用于预测的思维很可能能使得别人更好地完成做同样的工作。你写一本教科书，是因为你想改变世界，而不是因为你想赚钱。似乎大部分学生不想花钱在教科书上，因为他们经常只是使用一个学期。他们要不拥有一本过期的二手教科书，要不不使用课本而在网上搜索替代的资源。网络上几乎没有什么高质量教科书，有的话也很可能是不对的或者不完整的。所以我觉得我应该写一本在线课本，我不在意赚钱，每一个人都能阅读它，我不需要考虑别人能否支付得起价钱。所以我写了一本在线书籍，很快地很多人用上了它。当我放章节到网上的时候，它们会很快地获得高流量。当在线的东西是由有声誉的人写的高质量的东西的时候，人们就会喜欢上它们。所以之后我就创立了 OTexts 平台，以此来鼓励其他学者书写在线书记。我们确实有一些赚钱的计划。不过我们还没有真正的施行他们。书籍会一直保持免费，因为这是 OTexts 的一个重要的根本原则。

**Earo**: 你是一个作为政府和私人企业的咨询顾问。咨询工作和你的研究和教学是怎样联系在一起的？

**Rob**: 我的研究和咨询工作有着很密切的联系，它们互相依赖着对方。一个公司会带着一个解决不了的问题来找我。如果那个问题有现成的解决方案，我一般不会接单。我对可以用现成方案解决的常规咨询问题不感兴趣。不过如果问题看起来很难，没有明显的现成解决方案，我一般会接受那个咨询，因为那是一个有趣的问题，也可能引出可以发表的研究成果。理想的咨询工作应该可以引出论文。即使这不是直接和论文相关，咨询工作使得我对于商业和工业的实际问题保持关注，它们又引导我去做相关的研究。

比如说，很多年前，一个公司问我如何去解决一个预测问题，那个问题是关于成千上万个不同产品的月销售额的。他们想去预测每一个产品单独的销售额，以及零售商的总销售额或者单一产品类型的总销售额。我帮助他们解决这个问题，不过在那个时候我总是觉得，这里蕴含着一个理论问题，如何有效地预测分层时间序列。大约在那次咨询的 10 年之后，我写了第一篇关于分层时间序列模型的论文。现在我还在研究分层时间序列的预测的问题和工具。我发现我在用我的咨询的问题来推动我研究的方向。

另一个情况也可能发生。一个公司也许会带着一个我已经做过研究的问题。那么我也许会接受这个咨询工作，去搞清我的研究成果在实践中的有效程度。特别地，我想知道我的工具在哪些情况不适用，因为没有工具是完美的。这些缺陷也许会带给我另外的研究问题。我不把我的咨询经历完全地和我的研究分开。，因为我想接收研究类型的咨询工作。

有时，我会做一些免费的咨询工作，那些是对国家有利的，不过没有什么研究成分。有二十年，我参与到 Victoria 的 12 年级学生成绩换算工作（the scaling of all year 12 marks in Victoria）中。算法根据学生的成绩换算成一个能够各个学科之间比较的方式。这些标准化的成绩可以用于选择学生进入大学中。我免费地做这项工作，因为我认为这很重要。我也是澳大利亚统计局的一个顾问。我告诉他们为政府收集和分析数据的方法。

我的咨询工作在教育中也很有用，因为这给了我告诉给学生的故事，学生经常喜欢听到我做过的事情。每样事情 — 研究，咨询，教育 — 都结合在一起，我觉得很好。

![rob](https://cloud.githubusercontent.com/assets/18478302/24318161/e8619f18-113b-11e7-8895-9c5d5ff49034.JPG)