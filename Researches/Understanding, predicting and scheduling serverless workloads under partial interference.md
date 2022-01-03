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


"the coefficient of variance (CoV) of the latencies and the IPC vary over the partial interference scenarios." ([Zhao et al 2021:3](zotero://open-pdf/library/items/XCRAAQS7?page=3))

"Serverless functions are small in size and stateless" ([Zhao et al 2021:3](zotero://open-pdf/library/items/XCRAAQS7?page=3))

"Moreover, functions are stateless and spread over multiple machines in the cluster, leading to various interference locations." ([Zhao et al 2021:3](zotero://open-pdf/library/items/XCRAAQS7?page=3))

"3 the end-to-end perfor- 1○ o pro. mance relies on the function call path structure." ([Zhao et al 2021:3](zotero://open-pdf/library/items/XCRAAQS7?page=3))

"Serverless functions are short-lived" ([Zhao et al 2021:3](zotero://open-pdf/library/items/XCRAAQS7?page=3))

"implying that the later phase of the map and the shuffle phase are more sensitive to interference." ([Zhao et al 2021:4](zotero://open-pdf/library/items/XCRAAQS7?page=4))

"Partial interference triggers a chain reaction across the function call path and leads to 1.2 2" ([Zhao et al 2021:4](zotero://open-pdf/library/items/XCRAAQS7?page=4))

"partial interference affects the performance of functions in opposite ways: while 0.9 9tions is degraded by interference, the subsequent functions' performance on the call path instead improves." ([Zhao et al 2021:4](zotero://open-pdf/library/items/XCRAAQS7?page=4))

"Interference causes 1.2 2ns, resulting in increased local latency." ([Zhao et al 2021:4](zotero://open-pdf/library/items/XCRAAQS7?page=4))

"The colocation 1○- 5○ scheme should consider the end-to-end call path of each invocation to guarantee SLA." ([Zhao et al 2021:4](zotero://open-pdf/library/items/XCRAAQS7?page=4))

"Since function-level profiles keep much richer execution information than workload-level profiles [23], it becomes possible to build a performance predictor that is both accurate and lightweight." ([Zhao et al 2021:4](zotero://open-pdf/library/items/XCRAAQS7?page=4))

"Partial interference is generated by a random combination of the other workloads in" ([Zhao et al 2021:4](zotero://open-pdf/library/items/XCRAAQS7?page=4))

"FunctionBench [25]." ([Zhao et al 2021:5](zotero://open-pdf/library/items/XCRAAQS7?page=5))

"An accurate predicting model enables better QoS during actual execution." ([Zhao et al 2021:5](zotero://open-pdf/library/items/XCRAAQS7?page=5))

"Applying such predictors directly to serverless workloads would produce considerable errors (§ 6)." ([Zhao et al 2021:5](zotero://open-pdf/library/items/XCRAAQS7?page=5))

"aware incremental learning model" ([Zhao et al 2021:5](zotero://open-pdf/library/items/XCRAAQS7?page=5))

"produces QoS prediction results" ([Zhao et al 2021:5](zotero://open-pdf/library/items/XCRAAQS7?page=5))

"which is trained by learning on both offline data(➋➌) and sequentially-available online data(➒➓)" ([Zhao et al 2021:5](zotero://open-pdf/library/items/XCRAAQS7?page=5))

"We mitigate this problem using accurate functionlevel profiles and an elaborately designed predicting model." ([Zhao et al 2021:5](zotero://open-pdf/library/items/XCRAAQS7?page=5))

"Predict➋ containing both ningtecture-layer metrics" ([Zhao et al 2021:5](zotero://open-pdf/library/items/XCRAAQS7?page=5))

"Each partial interference scenario Incrementalode, which consists of" ([Zhao et al 2021:5](zotero://open-pdf/library/items/XCRAAQS7?page=5))

"two vectors capturing the spatial overlap and temporal overlap among functions." ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

"Function-level profiles, the partial interference code and labels constitute the initial training dataset." ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

"for its optimal placement" ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

"We adopt a non-intrusive method that only monitors the system-layer and microarchitecture-layer metrics of the application" ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

"In the system layer, we collect not only the configurations of resource allocation but also their actual utilization ratios, including the number of CPU cores, memory, network, memory bandwidth, and disk I/O." ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

"we record the instruction executionrelated measures of the CPU, which represent the execution status of the workload." ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

"the 99th percentile latency has a strong correlation with the IPC after the knee but varies significantly before that." ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

"Pearson Correlation Coefficient" ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

"Spearman Correlation Coefficient" ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

"The larger each coefficient is, the more the metrics are correlated with the ng" ([Zhao et al 2021:6](zotero://open-pdf/library/items/XCRAAQS7?page=6))

"we first prepare a small dataset of workload metrics and their corun QoS." ([Zhao et al 2021:7](zotero://open-pdf/library/items/XCRAAQS7?page=7))

"We design a regression model (denoted by 푅푀 ), which can predict the QoS of an arbitrary number of colocated workloads under partial interference." ([Zhao et al 2021:7](zotero://open-pdf/library/items/XCRAAQS7?page=7))

"The start delay vector (퐷퐴, 퐷 퐵 , 퐷퐶 , ...) codes the time overlap among workloads." ([Zhao et al 2021:7](zotero://open-pdf/library/items/XCRAAQS7?page=7))

"푖 푆 푖 푆 푖 푆n the system, and 푢푘푙 (1 ≤ 푙 ≤ 푆 , 1 ≤ 푘 ≤ 16) represents the 푘 th metric collected for 푖 's function on server 푙 ." ([Zhao et al 2021:7](zotero://open-pdf/library/items/XCRAAQS7?page=7))

"Hence, we choose the traditional ML approach, particularly Incremental RFR (IRFR), to build our model," ([Zhao et al 2021:8](zotero://open-pdf/library/items/XCRAAQS7?page=8))

"This mechanism is activated whenever a new workload is submitted or a previously submitted workload scales beyond the current function instances." ([Zhao et al 2021:8](zotero://open-pdf/library/items/XCRAAQS7?page=8))