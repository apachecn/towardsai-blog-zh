# 英国通过算法给学生打分的失败尝试

> 原文：<https://pub.towardsai.net/ofqual-algorithm-5ecbe950c264?source=collection_archive---------2----------------------->

![](img/4bb516f0ace08f0189a0f1002ef40621.png)

来源: [Pixabay](https://pixabay.com/) 上的 [JESHOOTScom](https://pixabay.com/en/users/JESHOOTScom-264599/)

## [人工智能](https://towardsai.net/p/category/artificial-intelligence)

## 为什么单靠工程不足以修复破碎的社会系统。

在新冠肺炎阻止学校正常运营和考试后，英国教育部试图用第三方机器学习算法给学生的 A-level 和 GCSE 考试打分。英国的 A-levels 在很大程度上决定了学生接受高等教育的机会，因此具有终身影响。应用算法根据学生在早期模拟考试中的个人表现(有些不相关和偏离)以及他们学校在前一年与其他学校的相对表现来预测学生的成绩。

许多批评家认为这种方法不准确、不公平，导致了显著的降级和对私立学校的偏爱。事实上，超过 40%的学生获得的分数低于老师的预测，相比之下，只有 2%的学生成绩有所提高(天堂，2020)。此外，大多数“降级”学生主要来自贫困的非白人社区。在公众的强烈反对下，政府被迫在成绩最终公布的前两天放弃了计划。

# Ofqual 算法

根据 Ofqual 技术报告(p83) 的[第 8 节，该算法旨在:](https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/909368/6656-1_Awarding_GCSE__AS__A_level__advanced_extension_awards_and_extended_project_qualifications_in_summer_2020_-_interim_report.pdf)

1.  查看学校该科目的历史成绩
2.  了解以前的成就如何映射到整个英格兰的最终结果
3.  基于此映射预测以前学生的成绩
4.  以同样的方式预测当前学生的成绩
5.  计算出与他们以前的成绩相匹配的学生比例
6.  创建一组目标等级
7.  根据学生的排名给他们分配粗略的分数
8.  根据学生的粗略分数给他们打分
9.  计算出国家等级界限和最终等级

更多细节，请点击这里查看林洋·坦尼森的技术演练。

# 区分工程问题和社会问题

这个有争议的分级模型不仅是英国公共部门(白芝浩，2020 年)科学管理过度热情应用系列[的最新一集，而且突出了人工智能广泛的社会，技术，经济，政治，法律和道德影响。在这种情况下，除了人口统计、社会流动性、不平等和偏见，工程和社会问题的相互作用也值得特别关注。](https://www.technologyreview.com/2020/08/05/1006034/the-uk-is-dropping-animmigration-algorithm-that-critics-say-is-racist/)

## ***工程问题***

在工程方面，还有两个问题。

首先，为什么要在一个具有终身影响的领域过早地在全国范围内实施？应用仅略好于主观人类评估的算法仍然是一种进步，并产生社会净效益。然而，通过增量试错来开发和扩展技术似乎更明智。

第二，为什么要完全取代评分和考试，而不是专注于增加和扩大教师的评分能力？人为输入或覆盖的机会可能会提高结果和利益相关者的接受度。

## **社会问题**

关于社会问题，在这种情况下，由公立和私立学校之间的差异所代表的不平等，不能仅用一种算法来解决(郝，2020)。算法很容易继承它们旨在修复的系统缺陷。因此，如果不积极有效地管理，就会产生自我实现的预言。公众意识、审查和透明度是消除偏见的关键第一步，但远非保证。

英国的评级崩溃表明…

> 如果你不正视相关的社会问题，再多的技术也无法改善现状。我们不能用工程解决方案来解决社会问题。
> 
> — Tse，Esposito，Goh，2019 年

这一原则不仅适用于简单的评级，还适用于所有涉及个人的领域，以及我们应用人工智能进行聚类、分类或预测的领域，如执法、移民政策、招聘或绩效评估。

***毕竟光靠算法是修复不了破碎的社交系统的。***

***关于作者:*** Yannique Hecht 作品在结合策略、客户洞察、数据、创新等领域。虽然他的职业生涯一直在航空、旅游、金融和技术行业，但他对管理充满热情。Yannique 专门开发 AI &机器学习产品商业化的策略。

*关注我上* [*中*](https://medium.com/@yannique) *或*[*LinkedIn*](https://www.linkedin.com/in/yannique/)*。*

***参考文献:***

*   西白芝浩(2020 年 8 月 20 日)。英国政府如何通过算法进行统治。经济学人。2020 年 9 月 1 日检索，来自[https://www . economist . com/Britain/2020/08/20/how the-British-government-rules-by-algorithm](https://www.economist.com/britain/2020/08/20/howthe-british-government-rules-by-algorithm)
*   郝，K. (2020 年 8 月 21 日)。英国考试的失败提醒我们，算法无法修复崩溃的系统。麻省理工科技评论。2020 年 9 月 1 日检索，来自[https://www . technology review . com/2020/08/20/1007502/uk-exam-algorithm-cant-fix broken-system/](https://www.technologyreview.com/2020/08/20/1007502/uk-exam-algorithm-cant-fixbroken-system/)
*   天堂，W. D. (2020 年 8 月 05 日)。英国放弃了一项移民算法，批评者称该算法带有种族主义色彩。麻省理工科技评论。2020 年 9 月 1 日检索，来自[https://www . technology review . com/2020/08/05/1006034/the-uk-is-dropping-anim migration-algorithm-that-critics-say-is-racistic/](https://www.technologyreview.com/2020/08/05/1006034/the-uk-is-dropping-animmigration-algorithm-that-critics-say-is-racist/)
*   坦尼森，J. (2020，8 月 16 日)。Ofqual 的评分算法是如何工作的？RPubs。于 2020 年 9 月 1 日从 https://rpubs.com/JeniT/ofqual-algorithm 检索到
*   Tse，T. C .，Esposito，m .，& Goh，D. (2019)。人工智能共和国:建立人类和智能自动化之间的联系。S.l .:狮冠出版公司。