# Understanding, predicting and scheduling serverless workloads under partial interference

>"Interference among distributed cloud applications can be classified into three types: full, partial and zero." ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1))


"We characterize the features of partial interference in serverless as exhibiting high volatility, spatial-temporal variation, and propagation." ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1))

"Small-sized functions increase the colocating density." ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1))

"Shortlived functions exacerbate the dynamicity of system runtime states." ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1))

"BG or LS functions usually process a request within seconds or milliseconds." ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1))

"coarse-grained" ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1))

"the many small-sized functions in serverless must share limited cores, memory bandwidth and LLC to improve resource efficiency." ([Zhao et al 2021:1](zotero://open-pdf/library/items/XCRAAQS7?page=1))

"The traditional prediction-based approaches (Table 2) that forecast mutual interference based on workload profiles can be adapted into a serverless system by treating each function as a separate application." ([Zhao et al 2021:2](zotero://open-pdf/library/items/XCRAAQS7?page=2))

"Compared with serverful workloads, small-sized Full stns are more prone to partial interference." ([Zhao et al 2021:2](zotero://open-pdf/library/items/XCRAAQS7?page=2))

"al we characterize the features of partial interference, which include the following:" ([Zhao et al 2021:2](zotero://open-pdf/library/items/XCRAAQS7?page=2))

"we also observe the predictability feature: diverse yet small-sized functions can expose more information about the inherent workload structure, and rich details at the function level can help to improve prediction accuracy." ([Zhao et al 2021:2](zotero://open-pdf/library/items/XCRAAQS7?page=2))

"Gsight identifies the temporality and spatiality of partial interference and encodes both the "function-server mappings" and the "time overlap" information in a prediction model" ([Zhao et al 2021:2](zotero://open-pdf/library/items/XCRAAQS7?page=2))

"our approach only requires the solo-run profiles of colocated functions and employs an incremental learning model that can converge quickly using the accurate function profiles." ([Zhao et al 2021:2](zotero://open-pdf/library/items/XCRAAQS7?page=2))

"we mainly study the tail latency and end-to-end average" ([Zhao et al 2021:2](zotero://open-pdf/library/items/XCRAAQS7?page=2))

"instructions per cycle (IPC) of LS workloads and the job completion times ( JCTs) of SC workloads under partial interference." ([Zhao et al 2021:3](zotero://open-pdf/library/items/XCRAAQS7?page=3))

"lo volatile" ([Zhao et al 2021:3](zotero://open-pdf/library/items/XCRAAQS7?page=3))

"Serverless functions are diverse in terms of execution behavior and resource consumption" ([Zhao et al 2021:3](zotero://open-pdf/library/items/XCRAAQS7?page=3))

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