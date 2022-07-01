# CCL2022：航旅纵横杯-面向领域问答的知识抽取评测（UMETRIP-QA）

> 北京航空航天大学
> 中航信移动科技有限公司

   当前互联网智能问答应用中，基于问题与答案对的检索式问答应用广泛。百度知道、知乎和各类问答平台的智能客服都会收集用户的高频问题和对应答案形成问答对数据库，再通过检索式问答方法来为用户提供准确的问询服务。因此，高效构建高质量的问答对数据库成为该应用的关键问题与难点。同时，互联网上存在着大量的非结构化或半结构化网页文本数据未被充分利用，如果能从这些数据中自动提取出问题和答案对数据，将为检索式问答提供极大助力。

   在自然语言处理相关技术中，阅读理解可以基于问题和文本数据，从文本数据中找出问题对应答案，得到问题答案对数据。该技术在保障较高的准确率下可实现问答对数据的高效构建，并经由人工简单验证实现高质量问答库构建。

   为此，我们组织本次测评任务，针对民航出行领域中信息动态更新频繁、用户出行问答需求旺盛及大量文本数据使用价值较低等问题，探索基于阅读理解技术实现从民航相关网页的文本数据中精准抽取出的问题和答案对。一方面有助于更好地组织管理民航领域常用知识，为用户提供更好的问询服务；另一方面也为基于阅读理解的问答对生成方法在其他领域的实践应用提供相关思路，探索垂直领域内的问答对构建范式。

任务组织者：

- 张日崇（北京航空航天大学）
- 王殿胜（中航信移动科技）

联系人：

- 张存旺（北航算法工程师）
- 贾泓昊（中航信移动科技工程师）
- 聂志捷（北航博士生）
- 王俊凯（北航硕士生）
- 曲文涛（北航硕士生）

# ！！！最新动态！！！
- 2022年6月5日，已经开放报名。
- 2022年7月1日，测试集所用的问题已经上传。
# 1 任务介绍

子任务一：篇章级答案检索

基于民航领域相关语料集合S，结合用户问句Q，采用信息检索相关模型与方法，返回与问句Q较相关或检索模型得分较高的N篇文章（Si, Sj, SK等）。本任务旨在探究模型篇章级信息检索能力，定位满足用户问句的答案所在相应文章。

子任务二：段落级答案抽取

在给定目标文章的段落集合P中，结合用户问句Q，识别包含问句答案的段落，模型可返回与答案相关或者评分较高的N个段落（Pi, Pj, Pk）。该任务关键在于评判模型对于答案段落精准定位的能力，作为篇章级答案检索的进一步细粒度定位，并为文本级答案抽取提供候选段落集合（P'）。

子任务三：细粒度文本级答案抽取

基于目标文章的段落集合P'，提供一个用户问句Qi，要求模型从段落集合P'中找到一个或者多个连续的片段作为答案，答案可以为词（Word）、短语（Phrase）或句子（Sentence）等，问句对应的答案集合A为不同类型答案的集合。此任务要求模型具有细粒度的文本理解和信息抽取能力。

# 2 测评数据

数据集在百度千言数据平台开放，数据说明以及下载请移步[数据详情](https://aistudio.baidu.com/aistudio/datasetdetail/149933)

# 3 评价标准

3.1 子任务一：篇章级答案检索

评价标准：模型输出结果的TopN（N=1，3，5）包含正确篇章的准确率。TopN的答案中包含正确篇章即可算该问句篇章答案检索正确。

3.2 子任务二：段落级答案抽取

评价标准：模型输出结果的TopN（N=1，3，5）包含正确段落的准确率TopN的答案中包含正确段落即可算该问句对应段落抽取正确。

3.3 子任务三：细粒度文本答案抽取

评价标准：

单个完整答案分数：
	精确率=预测答案与正确答案公共长度/预测段落长度
	召回率= 预测答案与正确答案公共长度/标注段落长度
	F1=2*精确率*召回率/（精确率+召回率）

多答案分数：
	对于部分问句，会有多个完整的答案，每个完整答案由多个答案片段组成。这种情况下每个完整答案单独计算精确率、召回率以及F1，然后取所有答案的F1值作为单个问句的答案分数。总的得分等于所有问句的F1的平均值。

# 4 赛程安排

    赛程主要时间节点如下
		• 评测任务发布：6月1日
		• 报名时间：6月1日—8月2日
		• 训练数据发布：6月1日
		• 测试数据发布：7月1日
		• 测试结果提交开放： 7月10日
		• 测评关闭：9月30日
		• CCL 2022评测研讨会：2022年10月14日—2022年10月16日

该测评任务将在[百度飞桨平台](https://aistudio.baidu.com/)中发布，届时参赛者可在该平台中注册报名比赛，并提交模型测试代码，实时查看该任务当前测评榜单，每个团队每天限提交三次模型代码进行测评。【评测以及榜单将在指定日期开放】

比赛详情页面链接：[CCL2022航旅纵横-领域知识问答测评（UMETRIP-QA）](https://aistudio.baidu.com/aistudio/competition/detail/313/0/introduction)

# 5 奖项设置

本次比赛每个任务独立进行排名，并根据排名颁发奖项。此外设置三个子任务奖励：

    子任务一：篇章级答案检索
		第一名：5000元
		第二名：3000元
		第三名：2000元

    子任务二：段落级答案抽取
		第一名：10000元
		第二名：5000元
		第三名：3000元

    子任务三：细粒度段落级答案抽取
		第一名：20000元
		第二名：7000元
		第三名：5000元

同时将由中国中文信息学会为本次评测获奖队伍提供荣誉证书。

# 6. 讨论交流

本次测评任务进行时，提供两个交流讨论方式：

- 飞桨比赛页面中的讨论区
- 比赛QQ群

<div align=left><img src="./image/README/CCL2022比赛交流群.jpg" alt="img" width=200" /></div>
