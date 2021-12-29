# Algorithm Applied on Workload Prediction
|Tittle|Algorithm|Idea|Read?|
|-----|----------|----|-----|
|**classical methods**|||
|An adaptive prediction approach based on workload pattern discrimination in the cloud|An adaptive approach|categorizes the workloads into different classes which are automatically assigned for different models according to workload features|
|TODO|Exponential Smoothing(ES)|||
|A Hierarchical Framework for Modeling and Forecasting Web Server Workload|Auto Regression(AR)|A linear combination of past values of the variable under consideration is used to forecast the value for upcoming time instances.||
|Dual time-scale distributed capacity allocation and load redirect algorithms for cloud systems|Moving Average(MA)|non-linear optimization The model is appropriate for time series exhbiting seasonal behavior only||
|Efficient autoscaling in the cloud using predictive models for workload forecasting|Autoregressive Integrated Moving Average(ARIMA)|also discussed the challenges involved in auto scaling in a cloud environment||
|Workload Prediction Using ARIMA Model and Its Impact on Cloud Applications’ QoS|Autoregressive Integrated Moving Average(ARIMA)|ARIMA on different confidence interval to predict web server workload|Y|
|Workload characterization and prediction in the cloud: A multiple time series approach|Hidden Markov Model|distinguish the temporal correlations in obtained clusters of VMs||
|A workload analysis of live event broadcast service in cloud|Regression techniques|the approach is based on simple statistical models that might not capture the patterns in more complex data||
|Workload characterization and prediction in the cloud: A multiple time series approach|multiple time series approch|The model does a grouping of similar applications's need in order to improve the accuracy of predictions||
|**machine learning methods**|||
|Support vector machines experts for time series forecasting|Self organizing map(SOM) and support vector machines(SVMs)|Self organizing map was used to cluster the data in different regions while SVMs were used to predict the future data||
|Referential kNN Regression for Financial Time Series Forecasting|$k$ Nearest Neighbors(kNN)|For financial time series prediction. kNNs are lazy learners and need high computational cost||
|Hierarchical neural networks based prediction and control of dynamic reconfiguration for multilevel embedded systems|the Neural network|used to model workload variations in multimidia designs||
|A cost-aware auto-scaling approach using the workload prediction in service clouds|Linear regression|the predicted workload was used to decide the type of scaling||
|Efficient resources provisioning based on load forecasting in cloud|Support Vector Regression(SVR) and Kalman smoother|It achieved high prediction accuracy||
|Combining time series prediction models using genetic algorithm to autoscaling Web applications hosted in the cloud infrastructure|Ensemble based model|It uses five different base prediction models. Each model is assigned a weight and contributes accordingly in predictions. The weight are assigned and optimized using genetic algorithm||
|Empirical prediction models for adaptive resource provisioning in the cloud|Neural network and Linear regression|||
|RVLBPNN: A Workload Forecasting Model for Smart Cloud Computing|back propagation learning algorithm|It adjusts the weights of model according to error trend.||
|A Predictive Method for Workload Forecasting in the Cloud Environment|neural network and steepest descent learning algorithm|suffers from high prediction errors.||
|Workload prediction in cloud using artificial neural network and adaptive differential evolution|neural network and adaptive differential evolution||Y|