
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=4 orderedList=false} -->

<!-- code_chunk_output -->

* [1. 禁忌搜索](#1-禁忌搜索)
	* [1.1. 问题举例](#11-问题举例)
		* [1.1.1. 问题流水作业调度问题](#111-问题流水作业调度问题)
		* [1.1.2. 问题工厂选址问题](#112-问题工厂选址问题)
	* [1.2. 基础概念](#12-基础概念)
		* [1.2.1. 历史背景](#121-历史背景)
		* [1.2.2. 禁忌搜索的提出](#122-禁忌搜索的提出)
		* [1.2.3. 搜索空间与邻域结构](#123-搜索空间与邻域结构)
		* [1.2.4. 禁忌](#124-禁忌)
		* [1.2.5. 鼓励策略](#125-鼓励策略)
		* [1.2.6. 算法模板](#126-算法模板)
		* [1.2.7. 算法终止条件](#127-算法终止条件)
		* [1.2.8. 随机禁忌搜索和候选列表](#128-随机禁忌搜索和候选列表)
	* [1.3. 拓展部分](#13-拓展部分)
		* [1.3.1. 强化](#131-强化)
		* [1.3.2. 多样性](#132-多样性)
		* [1.3.3. 允许不可行域](#133-允许不可行域)
		* [1.3.4. 替代和辅助目标函数](#134-替代和辅助目标函数)
		* [1.3.5. 研究发展方向(过时)](#135-研究发展方向过时)
	* [1.4. Tricks and Tips](#14-tricks-and-tips)
	* [1.5. 调参建议](#15-调参建议)
	* [1.6. 结论](#16-结论)
	* [1.7. 禁忌搜索用于CVRP中](#17-禁忌搜索用于cvrp中)
		* [1.7.1. 问题描述](#171-问题描述)
		* [1.7.2. 算法](#172-算法)
		* [1.7.3. 求解结果](#173-求解结果)

<!-- /code_chunk_output -->

# 1. 禁忌搜索

## 1.1. 问题举例
---
在讨论禁忌搜索算法前, 我们首先介绍两个组合优化中非常经典的问题,这两个问题存在一定的差异,这种差异在之后的算法介绍中将会被用到.
### 1.1.1. 问题流水作业调度问题
 n个作业{1,2,…,n}要在由m台机器组成的流水线上完成加工。每个作业加工的顺序都是固定从1到m, 加工作业i所需的时间分别为$t_{ij}$. 流水作业调度问题要求确定这n个作业的最优加工顺序，使得从第一个作业在机器$m_1$上开始加工，到最后一个作业在机器$m_m$上加工完成所需的时间最少。
### 1.1.2. 问题工厂选址问题
假设某地有n个可以开的工厂,m个顾客, 其需求分别是$d_i$, 每个工厂的开设都要不同的费用$f_j$，容量$K_j$, 而顾客为了满足自身的需求，到不同的工厂去消费也要不同的费用$x_{ij}$. 现在需要找出,在满足了所有顾客的需求的情况下, 每个工厂为每个客户的加工产品数$x_{ij}$, 使得总费用$\sum f_iy_i + \sum_{i \in I} \sum_{j \in J}c_{ij}x_{ij}$最小.这里要注意, 每家工厂都有自己的容量，不可以无限制的满足顾客的需求，若一个工厂剩余的容量比某个顾客的需求要小，那么它是无法满足顾客的需求；而对于顾客而言，他可选择多个工厂一起满足自己的需求。

对于这个问题, 有两个推论:
推论1: 对于每种工厂配置$\widetilde{y}$(开哪些工厂,不开哪些工厂), 都存在一个最优的$x(\widetilde{y})$使得在该配置下费用达到最小. 称y为loc var, 称x为flow var.
推论2: 问题解一定是一个超平面的极值, 超平面的定义如下(就是问题约束中和flow var相关的约束构成的平面)
$$ \sum_{j \in J} x_{ij} =d_i \\
\sum _{i\in I} x_{ij} \leq K_j \\
x_{ij} \geq 0\qquad i \in I, j \in J$$

## 1.2. 基础概念
---
### 1.2.1. 历史背景
禁忌搜索出现的时代是研究者刚刚发现大规模NP-hard问题几乎不能够使用精确算法有效求解的时代, 在意识到这个问题之后, 各种启发式算法被争相提出, 其中一类热门的算法以爬山算法为基础, 所谓爬山算法, 就是从一个可行解出发总是以得到比当前解更好的解为目标, 在当前解的基础上做出微小的改变进行尝试, 直到找不到更优解为止. 显然这种方法很容易困在局部最优中. 
### 1.2.2. 禁忌搜索的提出
最初禁忌算法在1986年被Glover提出的时候, 就是为了能够让爬山法能够克服局部最优的问题. 他提出在爬山法的基础上加上短程记忆来防止在局部最优附近徘徊, 加上长程记忆来强化有益的部分.其核心原则是通过允许没有进行对结果没有提升的动作来保证遇到局部最优时搜索能够继续; 通过短期记忆防止从局部最优走出的搜索返回——在一定迭代次数内记忆病禁止返回前几次动作, 这个短期记忆成为**禁忌表**.

### 1.2.3. 搜索空间与邻域结构
搜索空间和结构的设计, 是禁忌搜索算法最核心的步骤, 一个好的设计能够很好的发挥禁忌搜索的威力. 
**搜索空间** 搜索空间是包含所有可能被访问的解的空间. 搜索空间有时是直观的, 有时也没有那么直观. 对上文的问题1而言, 搜索空间中的一个点就是一个包含m个机器排班的方案, 这很直观; 但对于问题2而言, 我们既可以把超平面作为搜索空间, 也可以把loc var组成的空间作为搜索空间, 同时也可以把离散的loc var和连续的flow var整体作为搜索空间, 不同的搜索空间设计会导致不同的策略和难度. 搜索空间是否包含不可行解也是设计时需要考量的问题.
**邻域结构** 邻域结构的定义和搜索空间的定义高度相关. 对于一个当前解S, 可以通过局部的变换构成一个邻域解集N(S), 邻域结构包含了构造邻域的方法以及构成领域的邻域解集, 由搜索空间的定义的不同, 所允许的变换显然也将不同, 得到的邻域结构也会有所不同.
搜索空间和邻域结构的选择和构造应当充分利用到问题定义中所包含的信息, 使得求解尽可能简单.

### 1.2.4. 禁忌
禁忌是在爬山法的基础上产生的紧急搜索的最重要的概念之一. 禁忌的提出是为了有效避免在离开局部最优的过程中发生循环回到局部最优的情况. 禁忌的设置具体体现为实现一个具有短期记忆的禁忌表, 记录近几次移动的动作, 暂时禁止反向的动作发生, 在邻域结构中, 我们提到, 可以设计多种变换, 对当前解进行变化,因此, 对于禁忌表的设计, 也可以并推荐按照变换的种类不同建立多张禁忌表分别记录近期的变换动作.
标准的禁忌表通常通过一个定长的循环数组实现, 不过之后也有人提出过用非定长的数组等其他办法进行实现.

### 1.2.5. 鼓励策略
禁忌不是在所有情况下都是有利的, 有时候这种限制过于严苛, 可能会导致错过最优解, 因此有了鼓励策略(Aspiration Criteria). 最常用的鼓励策略就是当一个被禁忌的动作能够产生比当前更优解的时候, 这个动作会被采纳. 不论鼓励策略怎么设置, 核心的规则的就是在保证循环不发生的情况下, 禁忌可以被忽视.  
### 1.2.6. 算法模板
这里给出一个通用的禁忌搜索的模板.
$f(S)$是我们要最小化目标函数, 我们采用的实现版本总是选择最优可行动作来提升目标的质量, 这也是最常用的禁忌搜索的版本.
符号描述:
- $S$, 当前解
- $S^*$, 当前最优解
- $N(S)$, S的邻域
- $\tilde{N}(S)$, $N(S)$的准许的子集(非禁忌的部分或禁忌但是被鼓励策略允许的部分)
- T, 禁忌表

-----
**Init**
Choose (construct) an initial solution S0.
Set S \gets S_0, f^* \gets f (S_0), S^* \gets S_0, T\gets \emptyset.
**Search**
while *termination crriterion not satisfied* do 
- select S in $ argmin_{s' \in \tilde{N}(S)}|f(S')|$;
- if $f(S) < f^*$, then set $f^* \gets f(S), S^* \gets S$;
- record tubu for the current move in T(delete the oldest if neccessary).

endwhile

-----

### 1.2.7. 算法终止条件
常用的有以下几种:
- 达到固定迭代次数或时长
- 达到没有改进的连续迭代次数上限
- 目标函数值达到某个阈值

### 1.2.8. 随机禁忌搜索和候选列表
随机禁忌搜索的随机性主要体现在对邻域解的选择上. 在有的问题中, 由于问题的领域空间过大或者目标函数的计算过于复杂, 对所有邻域空间的解进行计算会导致计算量过大不能够接受, 这时可以随机选择有些可能性较大的解进行验证. 候选列表的提出原因和随机方法一致, 选择较少的若干个方案进行结果的验证, 可以说, 随机禁忌搜索就是候选列表方法的一个实例. 但是,候选列表和随机选择都存在可能会错过最优解的问题, 因此在选择的时候需要慎重.

## 1.3. 拓展部分
### 1.3.1. 强化
对于可能出现最优解的区域, 对于人来说, 人们常会更仔细的去搜索, 将这种思想引入到算法中,就是强化的核心. 在禁忌搜索中, 如何在比较可信的空间进行更加彻底的搜索以确定这个区域的最优解被找到.对于这个问题, 主要有两类方法, 一种方法是将频繁出现在当前最优解中的这部分固定, 对于剩下的部分重新进行搜索; 另一种方法是加入更多的变化方式使得邻域结构更加丰富.

### 1.3.2. 多样性
对于大多数邻域搜索算法来说, 一个突出的问题就是这类方法的搜索都太过局部了, 局部对算法的吸引力过强显然会导致可能错过最优解. 多样性是一种强制算法去搜索之前很少或没有搜索过的搜索空间的一种机制, 它通常通过搜索过程中的长程记忆性来实现,例如使用频率记忆来记录当前解中以及当前的动作影响到的这些解的部分在之前迭代中出现的次数.

主要的多样性技术有两种, 一种称为重启多样性, 这种技术将一些很少出现的解部分加入到当前解中, 然后从这个点重新开始搜索; 另一种称为连续性多样性, 将多样性的思想直接整合进常规的搜索过程.

合适的搜索多样性设计可能是禁忌搜索设计中最重要的步骤, 也是如果计算结果没有达到预期时首先需要检查的部分.
### 1.3.3. 允许不可行域
复杂约束可能导致搜索空间太小或结构复杂不利于搜索, 因此对于复杂约束, 约束松弛是个很好的办法. 在禁忌搜索中可以通过在搜索空间定义时松弛该约束, 并在目标函数中加上对违反这个约束的惩罚项来实现, 其中目标函数的约束惩罚项的权重, 可以是动态适应的, 随着搜索接近结束而增大, 随着最近迭代中没有出现违反约束的次数增加而降低等.

### 1.3.4. 替代和辅助目标函数
不同的问题的目标函数不同, 有的问题的目标函数可能不利于搜索.

对于目标函数计算复杂的问题, 可以构造一个辅助目标函数, 提高搜索的效率, 先从搜索空间中选出少量的候选解列表, 再计算它们的真正的目标函数进行比较. 辅助目标函数可以是分支定界中的下界等较容易计算的函数.
对于另一类问题, 目标函数可能不能够提供足够的有效信息, 例如在问题2中, 如果工厂开工的固定费用远高于运输费用时. 在这种情况下, 需要有个辅助函数, 能够引导搜索向降低工厂数量的方向进行搜索, 比如对于生产数量小的工厂, 在之后的迭代中倾向于关闭.

### 1.3.5. 研究发展方向(过时)
目前对禁忌搜索的研究,很大程度上集中在如何让算法更加高效上, 这包括如何更好的利用信息构造初始解, 也包括了如何选择更加强大的邻域操作和并行搜索策略. 另一个研究热点在禁忌搜索的杂交上.

目前, 禁忌搜索的文章也开始从传统的应用领域(图论问题,时间计划,车辆路径)向连续优化方向发展.
## 1.4. Tricks and Tips
![](http://cdn.hustcaid.com/Frxt_K_Hthcs-Zr0ABd8cT7VpYUy.png)

更高级的建议:
1. 对于复杂约束问题, 考虑引入允许非可行域的机制,使得搜索空间更加有意义.
2. 邻域结构的构造非常重要, 如果得到的结果不好,需要考虑是否是邻域结构构造过于简单.
3. 搜集结果进行统计,可以通过记录局部最优解, 分析强化和多样性的机制的效果
4. 对于合理的数据集, 单步跟随算法, 看算法的运行是否符合预期.
5. 重视多样性的设计.
6. 对不同的参数进行测试, 有的搜索过程对参数敏感, 可以通过对参数进行广泛测试后, 集中在一个小的参数区间, 进一步调试.

对于随机禁忌搜索, 如果结果比较平庸, 可以在算法结束前加入一个强化阶段, 对随机禁忌搜索给出的最优解的邻域进行进一步搜索.

## 1.5. 调参建议
![](http://cdn.hustcaid.com/FglZgV-K1ALJn9TyHPcHdXM-pJbC.png)

## 1.6. 结论
禁忌搜索的新内容: 使用禁忌表避免坠入局部最优(短程记忆性)

禁忌搜索的重要技术点:
- 搜索空间&邻域结构设计
- 强化&多样性策略

搜索空间&邻域结构: 充分利用问题的信息和问题的特点. 邻域结构的设计目标, 简洁不简单

强化: 固定可信结构, 对其他结构进行更加细致的搜索

多样性: 利用长程记忆性, 将很少访问的搜索空间加入到搜索中


## 1.7. 禁忌搜索用于CVRP中
### 1.7.1. 问题描述

### 1.7.2. 算法
### 1.7.3. 求解结果