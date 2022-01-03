# Understanding, predicting and scheduling serverless workloads under partial interference
## Introduction

>"Interference among distributed cloud applications can be classified into three types: full, partial and zero." ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1))

分布式的云应用之间的相互影响可以被分成三种类型：
- Full
- Partial
- Zero

![[Pasted image 20220103200140.png]]

通常Full的互影响被研究的比较多，而本文研究的是欠分析的Partial场景下的互影响

>"We characterize the features of partial interference in serverless as exhibiting high volatility, spatial-temporal variation, and propagation." ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1))

根据以上特点，论文将商业的serverless应用总结为三种类型：
- scheduled-background（BG）
- short-term computing（SC）
- latency-sensitive（LS）

![[Pasted image 20220103200623.png]]

>"Small-sized functions increase the colocating density." ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1))

>"Shortlived functions exacerbate the dynamicity of system runtime states." ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1))

>"the many small-sized functions in serverless must share limited cores, memory bandwidth and LLC to improve resource efficiency." ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1))

在空间维度上的small-sized以及在时间维度上trigger的任意性以及例如BG或者LS的function会在几秒甚至几微秒内运行完，导致serverless system有非常多的状态以及不确定性. 并且由于这些小的任务存在，导致它们不得不共用核心、内存带宽以及Cache以提高资源的效率，这也极大的增加了colocation的密度

> "coarse-grained" ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1)): **粗粒度的**

___

>"The traditional prediction-based approaches that forecast mutual interference based on workload profiles can be adapted into a serverless system by treating each function as a separate application." ([Zhao et al 2021:2](zotero://open-pdf/library/items/XCRAAQS7?page=2))

>"Compared with serverful workloads, small-sized Full stns are more prone to partial interference." ([Zhao et al 2021:2](zotero://open-pdf/library/items/XCRAAQS7?page=2))

传统的基于预测的方法都是利用 workload 的 profile，这通常需要耗费大量资源在profiling阶段，并且预测的结果非常容易受到 partial interference 的影响。**论文提出的方法是对每一个 function 做 profiling

因此，论文首先对 partial interference 的特征进行了总结（通过实验和统计）:
- High volatility: 
	"Serverless functions are diverse in terms of execution behavior and resource consumption" ([Zhao et al 2021:3](zotero://open-pdf/library/items/XCRAAQS7?page=3))
- Spatial variation
	Serverless functions are small in size and stateless, making partial interference spatially varied.
	function 的 无状态性并且会在多个物理机器上流转制造了多种多样的interference
	并且，端到端的表现依赖于函数的调用路径结构（call path structure）
- Temporal variation
	Serverless functions are short-lived, making partial interference temporally varied.
	具体来说，function 在执行的每个阶段对于 interference 的敏感程度是不一样的
- Hotspot Propagation
	Partial interference triggers a chain reaction across the function call path and leads to diametrically opposite effects.
- Restoring Propagation
	The local control of partial interference suffers from impact propagation.
	
![[Pasted image 20220103204137.png]]

并且通过实验得出了相对于整个workload，这些小的function会提供更多信息供提高预测的准确率，因此 partial interference 也是 **predictablity** 的

>"we also observe the predictability feature: diverse yet small-sized functions can expose more information about the inherent workload structure, and rich details at the function level can help to improve prediction accuracy." ([Zhao et al 2021:2](zotero://open-pdf/library/items/XCRAAQS7?page=2))

---

>"Gsight identifies the temporality and spatiality of partial interference and encodes both the "function-server mappings" and the "time overlap" information in a prediction model" ([Zhao et al 2021:2](zotero://open-pdf/library/items/XCRAAQS7?page=2))

>"our approach only requires the solo-run profiles of colocated functions and employs an **incremental learning model** that can converge quickly using the accurate function profiles." ([Zhao et al 2021:2](zotero://open-pdf/library/items/XCRAAQS7?page=2))

论文对于相关领域的研究有如下的贡献：
- 针对 colocation 的分布式 workload 分析了它的特征并且提出了一种时空重叠的编码（spatial-temporal overlap）
- 提出了使用 function-level 的 profiling 以获得更快的收敛以及更高的准确性（具体来说，所用的metrix仅仅监测了system-layer和microarchitecture-layer
- 设计了Gosight，可以在保证QoS的前提下对于BG、SC和LS的负载给出高准确性的预测

___
>"we mainly study the tail latency and end-to-end average instructions per cycle (IPC) of LS workloads and the job completion times ( JCTs) of SC workloads under partial interference." ([Zhao et al 2021:3](zotero://open-pdf/library/items/XCRAAQS7?page=3))

对于LS的负载，主要关注它的尾延时和端到端的平均IPC，对于SC负载主要关注它的完成时间

---
>"Applying such predictors directly to serverless workloads would produce considerable errors ." ([Zhao et al 2021:5](zotero://open-pdf/library/items/XCRAAQS7?page=5))

常用的预测器主要关注 full interference，直接把这些方法应用到partial的场景下会产生errors

## Design
![[Pasted image 20220103210457.png]]

### offline training
 >"The core of the predictor is an **incremental learning model** which is trained by learning on both offline data(➋➌) and sequentially-available online data(➒➓)" ([Zhao et al 2021:5](zotero://open-pdf/library/items/XCRAAQS7?page=5))

增量的学习模型首先利用有限的历史数据产生一个模型，然后持续的学习，提升预测准确率，但是模型在一开始是容易underfiting的

>"We mitigate this problem using accurate functionlevel profiles and an elaborately designed predicting model." ([Zhao et al 2021:5](zotero://open-pdf/library/items/XCRAAQS7?page=5))

解决这种 underfiting 论文使用的两种方法，首先，对于每个function首先产生一次solo-run的检测，并且同时产生 system-layer 和 microarchitecutre 的数据。然后，再对这些工作负载施加 partial interference 以产生训练用的label

>"Each partial interference scenario Incrementalode, which consists of two vectors capturing the spatial overlap and temporal overlap among functions." ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

对于每一 partial interference 的场景，都产生两个向量用于描述时间重叠和空间重叠。空间重叠向量描述了函数间的 codeployment locations，时间重叠向量描述了函数间的时间重叠情况

>"Function-level profiles, the partial interference code and labels constitute the initial training dataset." ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

**accurate function-level profile**以及 **精心设计的模型（coding方法)** 使得initial model 的 underfiting不那么严重

### online predicting

在线模块里，当用户提交了一个新的serverless workload之后：
- 系统首先将functions执行 solo-run 以 profiling
- schduling算法会通过预测模型迭代的寻找其最优的放置策略
- 每一次迭代中，预测模型都会根据它的solo-run数据和partial interference编码预测出它的QoS
- 当functions真正开始运行的时候，系统会检测它的各项数据用于更新模型

### profiling


>"We adopt a non-intrusive method that only monitors the system-layer and microarchitecture-layer metrics of the application" ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

>"In the system layer, we collect not only the configurations of resource allocation but also their actual utilization ratios, including the number of CPU cores, memory, network, memory bandwidth, and disk I/O." ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

>"we record the instruction executionrelated measures of the CPU, which represent the execution status of the workload." ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

___

![[Pasted image 20220103215951.png]]

>"the 99th percentile latency has a strong correlation with the IPC after the knee but varies significantly before that." ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

这表明一个良好训练的IPC预测模型在“keen”之后尾延时预测预测也会有高的准确性

![[Pasted image 20220103220125.png]]

>"Pearson Correlation Coefficient" ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

>"Spearman Correlation Coefficient" ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

>"The larger each coefficient is, the more the metrics are correlated with the ng" ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

___
>"we first prepare a small dataset of workload metrics and their corun QoS." ([Zhao et al 2021:7](zotero://open-pdf/library/items/XCRAAQS7?page=7))

>"We design a regression model (denoted by 푅푀 ), which can predict the QoS of an arbitrary number of colocated workloads under partial interference." ([Zhao et al 2021:7](zotero://open-pdf/library/items/XCRAAQS7?page=7))

The model for predicting application A's performance under the interference of $B, C, ...(i.e., P_{A\cup\{B,C,...\}})$ is described as follows:

![[Pasted image 20220103220309.png]]


"Hence, we choose the traditional ML approach, particularly Incremental RFR (IRFR), to build our model," ([Zhao et al 2021:8](zotero://open-pdf/library/items/XCRAAQS7?page=8))

本论文所用的回归方法是**IRFR算法**

>"This mechanism is activated whenever a new workload is submitted or a previously submitted workload scales beyond the current function instances." ([Zhao et al 2021:8](zotero://open-pdf/library/items/XCRAAQS7?page=8)

无论是新的workload到来还是先前的workload变化该方法都是有效的