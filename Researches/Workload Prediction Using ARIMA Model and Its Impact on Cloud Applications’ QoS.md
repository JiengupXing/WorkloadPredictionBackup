# Workload Prediction Using ARIMA Model and Its Impact on Cloud Applications’ QoS

## Abstract

>"This problem can be solved with proactive dynamic provisioning of resources, which can estimate the future need of applications in terms of resources and allocate them in advance," ([Calheiros et al 2015:449](zotero://open-pdf/library/items/MW2JR4ED?page=1))

论文指出在对QoS影响比较小的情况下（满足QoS metrix的接受阈值），利用ARIMA方法做负载预测可以得到91%的平均准确率

## Introduction

>"However, one issue that arises from the transition to a SaaS model is the fact that the pattern of access to the application varies according to the time of the day, day of the week, and part of the year." ([Calheiros et al 2015:449](zotero://open-pdf/library/items/MW2JR4ED?page=1))

SaaS业务实际上通常是变化多端的

>"based on workload behavior patterns such as request arrival rate and service time distributions." ([Calheiros et al 2015:449](zotero://open-pdf/library/items/MW2JR4ED?page=1))

根据负载的行为特征例如请求到达情况和服务时间分布等可以来预测负载在未来的行为

>"This challenge has been tackled mainly via reactive approaches [3], [4], [5]—which increase or decrease resources when predefined thresholds are reached—or via [[proactive]] approaches [6], [7], [8]— which react to future load variations before their occurrence" ([Calheiros et al 2015:449](zotero://open-pdf/library/items/MW2JR4ED?page=1))
>
>"The limitation of reactive platforms is that they react to changes in workload only after the change in utilization and throughput is observed in the system." ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2))

一般来说解决负载预测的问题所用的方法分为reactive的（即发生之后再反应）以及[[proactive]]的（即防患于未然，对负载进行预测，然后在用户感受不到的情况下对资源分配进行调整）

>"determines **how many requests per second** are expected in the near future" ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2))

本文进行预测的metrix主要是每秒的请求数

### Contributions
- We propose, design, and develop a workload prediction module using the ARIMA model which is fed into the [[queueing model]] for calculating the required VM configuration." ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2)). Our work applies feedback from latest observed loads to update the model on the run. The predicted load is used to dynamically provision VMs in an elastic Cloud environment for serving the predicted requests taking into consideration QoS parameters such as response time and rejection rate;

- We conduct an evaluation of the impact of the achieved accuracy in terms of efﬁciency in resource utilization and QoS of user requests.

## Related Work

>"studies [13], [14] show that web and data center workloads tend to present behavior that can be effectively captured by time series-based models." ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2))

>"Tran et al. [14] applied the ARIMA model for prediction of server workloads." ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2))

>"PachecoSanchez et al. [16] apply a Markovian model to predict server performance in Clouds." ([Calheiros et al 2015:451](zotero://open-pdf/library/items/MW2JR4ED?page=3))

>"Roy et al. [13] apply the ARMA model for workload prediction in Clouds with the goal of minimizing cost," ([Calheiros et al 2015:451](zotero://open-pdf/library/items/MW2JR4ED?page=3))

## System And Application Models

这一节主要是描述了研究要解决的问题模型，包括一些业务的情况说明，可以看出来，真实的业务场景是非常复杂的，有的时候物理机器会由第三方来提供，SaaS服务由提供商作为中间层，提供带有保障的服务给用户。

>"The PaaS in turn interacts with an IaaS provider that can be a third party provider." ([Calheiros et al 2015:451](zotero://open-pdf/library/items/MW2JR4ED?page=3))

## System Architecture

>"One of the key characteristics of Clouds is elasticity" ([Calheiros et al 2015:451](zotero://open-pdf/library/items/MW2JR4ED?page=3))

云服务的一大特点就是可伸缩性，用户会根据自己当时的需求来要求动态变化占用的资源，同时用户指定的应用也存在周期性的变化其负载情况

![[Pasted image 20211229200754.png]]

1. Application Provisioner
负责根据用户的访问请求分配足够的VMs处理请求，同时会根据*Load Predictor and Performance Modeler*的预测调整分配的数量

>"It also keeps track of the performance of the VMs." ([Calheiros et al 2015:451](zotero://open-pdf/library/items/MW2JR4ED?page=3))

2. Load Predictor and Performance Modeler
核心模块

>"which, based on the predicted arrival rate of requests, return the minimum number of VMs that is able to meet the QoS metrics." ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

3. Workload Analyzer

>"Analyzer Generates an estimation of future demand for the application." ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

"a queueing model can be built for each application offered to end users as a service." ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

"ARIMA has been chosen for the implementation of our module because the underlying workload fits well in the model:" ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

"the historical workload data is fed into the Workload Analyzer, where it fits the ARIMA model on them." ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

"with one time-interval in advance" ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

"It is implemented Control so that at the next prediction cycle, the actual number of requests (obtained from the original dataset) is added to the time series used in prediction while discarding the oldest value." ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

"initiated based on the Box-Jenkins method" ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

"This transformation is achieved by differencing the original time series. The number of times the original time series has to be differenced until it becomes stationary constitutes the d parameter of the ARI M A(p; d; q) model." ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

"The values of q and p are determined by analyzing the autocorrelation and partial autocorrelation plots of the historical data, respectively. In the context of this work, historical data means the observed number of requests per second received by the system in some past time interval." ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

"The autocorrelation plot is used to determine how random a dataset is." ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

"Using the above method to determine the terms p, d, and q of the ARIMA model, the historical workload information is fit to the model to be used for prediction of future workload values." ([Calheiros et al 2015:453](zotero://open-pdf/library/items/MW2JR4ED?page=5))

"The length of this buffer, which corresponds to the number of time intervals in past affecting the current prediction value, is configured at the start of the system based on characteristics of the application workload (number of received requests per second)." ([Calheiros et al 2015:453](zotero://open-pdf/library/items/MW2JR4ED?page=5))

"It accepts a time series from the ARIMAWorkloadAnalizer and prepares it for submission to the statistic engine, where ARIMA model is fitted on them." ([Calheiros et al 2015:453](zotero://open-pdf/library/items/MW2JR4ED?page=5))

"We adopted the fitting process from R, which implements the Hyndman-Khandakar algorithm [20]." ([Calheiros et al 2015:453](zotero://open-pdf/library/items/MW2JR4ED?page=5))

"(i) determination of the number of differencing steps of the model (parameter d); (ii) actual differentiation of the time series d times; and (iii) selection of the best fit model." ([Calheiros et al 2015:453](zotero://open-pdf/library/items/MW2JR4ED?page=5))

"The method used by R for the first stage applies successive Kwiatkowski-Phillips-Schmidt-Shin (KPSS) tests [22] to determine d." ([Calheiros et al 2015:453](zotero://open-pdf/library/items/MW2JR4ED?page=5))

"Because the propose method predicts one time interval ahead, it has complexity O(p), where p is the order of the autoregressive component of the ARIMA model." ([Calheiros et al 2015:453](zotero://open-pdf/library/items/MW2JR4ED?page=5))

"1-hour intervals" ([Calheiros et al 2015:453](zotero://open-pdf/library/items/MW2JR4ED?page=5))

"At runtime, the model is constantly updated: whenever new requests arrive, they are incorporated to the time series and older data is removed from the time series in the same amount." ([Calheiros et al 2015:454](zotero://open-pdf/library/items/MW2JR4ED?page=6))

"Pa The accuracy of the prediction is evaluated using varl ious error metrics." ([Calheiros et al 2015:454](zotero://open-pdf/library/items/MW2JR4ED?page=6))

"The particularities of the workload is one factor to be considered when selecting a prediction technique, as different techniques can present different performance depending on the characteristic of each workload." ([Calheiros et al 2015:455](zotero://open-pdf/library/items/MW2JR4ED?page=7))

"Sladescu et al. [7] successfully utilized artificial neural networks to predict workloads bursts in auction websites." ([Calheiros et al 2015:455](zotero://open-pdf/library/items/MW2JR4ED?page=7))