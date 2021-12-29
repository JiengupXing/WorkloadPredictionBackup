---
title: Workload Prediction Using ARIMA Model and Its Impact on Cloud Applications’ QoS
authors: Rodrigo N. Calheiros, Enayat Masoumi, Rajiv Ranjan, Rajkumar Buyya
year: 2015
---

**Extracted Annotations (2021/12/29 下午7:32:01)**

"This problem can be solved with proactive dynamic provisioning of resources, which can estimate the future need of applications in terms of resources and allocate them in advance," ([Calheiros et al 2015:449](zotero://open-pdf/library/items/MW2JR4ED?page=1))

"However, one issue that arises from the transition to a SaaS model is the fact that the pattern of access to the application varies according to the time of the day, day" ([Calheiros et al 2015:449](zotero://open-pdf/library/items/MW2JR4ED?page=1))

"of the week, and part of the year." ([Calheiros et al 2015:449](zotero://open-pdf/library/items/MW2JR4ED?page=1))

"circumvent" ([Calheiros et al 2015:449](zotero://open-pdf/library/items/MW2JR4ED?page=1))

"based on workload behavior patterns such as request arrival rate and service time distributions." ([Calheiros et al 2015:449](zotero://open-pdf/library/items/MW2JR4ED?page=1))

"This challenge has been tackled mainly via reactive approaches [3], [4], [5]—which increase or decrease resources when predefined thresholds are reached—or via proactive approaches [6], [7], [8]— which react to future load variations before their occurrence" ([Calheiros et al 2015:449](zotero://open-pdf/library/items/MW2JR4ED?page=1))

"determines how many requests per second are expected in the near future" ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2))

"In contrast to this approach, we" ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2))

"apply the ARIMA model to predict the future application workload behavior, which is fed into the queueing model for calculating the required VM configuration." ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2))

"The limitation of reactive platforms is that they react to changes in workload only after the change in utilization and throughput is observed in the system." ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2))

"Considering that changes in the workload typically follow patterns that are time-dependent" ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2))

"Islam et al. [8] apply Artificial Neural Networks (ANN) and linear regression for prediction of resources required for applications." ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2))

"studies [13], [14] show that web and data center workloads tend to present behavior that can be effectively captured by time series-based models." ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2))

"Tran et al. [14] applied the ARIMA model for prediction of server workloads." ([Calheiros et al 2015:450](zotero://open-pdf/library/items/MW2JR4ED?page=2))

"PachecoSanchez et al. [16] apply a Markovian model to predict server performance in Clouds." ([Calheiros et al 2015:451](zotero://open-pdf/library/items/MW2JR4ED?page=3))

"Roy et al. [13] apply the ARMA model for workload prediction in Clouds with the goal of minimizing cost," ([Calheiros et al 2015:451](zotero://open-pdf/library/items/MW2JR4ED?page=3))

"The PaaS in turn interacts with an IaaS provider that can be a third party provider." ([Calheiros et al 2015:451](zotero://open-pdf/library/items/MW2JR4ED?page=3))

"One of the key characteristics of Clouds is elasticity" ([Calheiros et al 2015:451](zotero://open-pdf/library/items/MW2JR4ED?page=3))

"It also keeps track of the performance of the VMs." ([Calheiros et al 2015:451](zotero://open-pdf/library/items/MW2JR4ED?page=3))

"which, based on the predicted arrival rate of requests, return the minimum number of VMs that is able to meet the QoS metrics." ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

"Analyzer Generates an estimation of future demand for the application." ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

"M a queueing model can be built for each application offered to end users as a service." ([Calheiros et al 2015:452](zotero://open-pdf/library/items/MW2JR4ED?page=4))

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