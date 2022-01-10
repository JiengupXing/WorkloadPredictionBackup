# Box–Jenkins method

In [time series analysis](https://en.wikipedia.org/wiki/Time_series_analysis "Time series analysis"), the **Box–Jenkins method,**[\[1\]](https://en.wikipedia.org/wiki/Box%E2%80%93Jenkins_method#cite_note-1) named after the [statisticians](https://en.wikipedia.org/wiki/Statistician "Statistician") [George Box](https://en.wikipedia.org/wiki/George_Box "George Box") and [Gwilym Jenkins](https://en.wikipedia.org/wiki/Gwilym_Jenkins "Gwilym Jenkins"), applies [autoregressive moving average](https://en.wikipedia.org/wiki/Autoregressive_moving_average "Autoregressive moving average") (ARMA) or [autoregressive integrated moving average](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average "Autoregressive integrated moving average") (ARIMA) models to find the best fit of a time-series model to past values of a [time series](https://en.wikipedia.org/wiki/Time_series "Time series").

## Modeling approach\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=1 "Edit section: Modeling approach")\]

The original model uses an iterative three-stage modeling approach:

1.  _[Model identification](https://en.wikipedia.org/wiki/Model_identification "Model identification") and [model selection](https://en.wikipedia.org/wiki/Model_selection "Model selection")_: making sure that the variables are [stationary](https://en.wikipedia.org/wiki/Stationary_process "Stationary process"), identifying [seasonality](https://en.wikipedia.org/wiki/Seasonality "Seasonality") in the dependent series (seasonally differencing it if necessary), and using plots of the [autocorrelation (ACF)](https://en.wikipedia.org/wiki/Autocorrelation "Autocorrelation") and [partial autocorrelation (PACF)](https://en.wikipedia.org/wiki/Partial_autocorrelation "Partial autocorrelation") functions of the dependent time series to decide which (if any) autoregressive or moving average component should be used in the model.
2.  _[Parameter estimation](https://en.wikipedia.org/wiki/Parameter_estimation "Parameter estimation")_ using computation algorithms to arrive at coefficients that best fit the selected ARIMA model. The most common methods use [maximum likelihood estimation](https://en.wikipedia.org/wiki/Maximum_likelihood_estimation "Maximum likelihood estimation") or [non-linear least-squares estimation](https://en.wikipedia.org/wiki/Non-linear_least-squares_estimation "Non-linear least-squares estimation").
3.  _[Statistical model checking](https://en.wikipedia.org/wiki/Statistical_model_validation "Statistical model validation")_ by testing whether the estimated model conforms to the specifications of a stationary univariate process. In particular, the residuals should be independent of each other and constant in mean and variance over time. (Plotting the mean and variance of residuals over time and performing a [Ljung–Box test](https://en.wikipedia.org/wiki/Ljung%E2%80%93Box_test "Ljung–Box test") or plotting autocorrelation and partial autocorrelation of the residuals are helpful to identify misspecification.) If the estimation is inadequate, we have to return to step one and attempt to build a better model.

The data they used were from a gas furnace. These data are well known as the Box and Jenkins gas furnace data for benchmarking predictive models.

Commandeur & Koopman (2007, §10.4)[\[2\]](https://en.wikipedia.org/wiki/Box%E2%80%93Jenkins_method#cite_note-2) argue that the Box–Jenkins approach is fundamentally problematic. The problem arises because in "the economic and social fields, real series are never stationary however much differencing is done". Thus the investigator has to face the question: how close to stationary is close enough? As the authors note, "This is a hard question to answer". The authors further argue that rather than using Box–Jenkins, it is better to use state space methods, as stationarity of the time series is then not required.

## Box–Jenkins model identification\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=2 "Edit section: Box–Jenkins model identification")\]

### Stationarity and seasonality\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=3 "Edit section: Stationarity and seasonality")\]

The first step in developing a Box–Jenkins model is to determine whether the [time series](https://en.wikipedia.org/wiki/Time_series "Time series") is [stationary](https://en.wikipedia.org/wiki/Stationary_process "Stationary process") and whether there is any significant [seasonality](https://en.wikipedia.org/wiki/Seasonality "Seasonality") that needs to be modelled.

#### Detecting stationarity\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=4 "Edit section: Detecting stationarity")\]

Stationarity can be assessed from a [run sequence plot](https://en.wikipedia.org/wiki/Run_sequence_plot "Run sequence plot"). The run sequence plot should show constant location and [scale](https://en.wikipedia.org/wiki/Scale_(ratio) "Scale (ratio)"). It can also be detected from an [autocorrelation plot](https://en.wikipedia.org/wiki/Autocorrelation_plot "Autocorrelation plot"). Specifically, non-stationarity is often indicated by an autocorrelation plot with very slow decay.

#### Detecting seasonality\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=5 "Edit section: Detecting seasonality")\]

Seasonality (or periodicity) can usually be assessed from an autocorrelation plot, a [seasonal subseries plot](https://en.wikipedia.org/wiki/Seasonal_subseries_plot "Seasonal subseries plot"), or a [spectral plot](https://en.wikipedia.org/wiki/Spectral_plot "Spectral plot").

#### Differencing to achieve stationarity\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=6 "Edit section: Differencing to achieve stationarity")\]

Box and Jenkins recommend the differencing approach to achieve stationarity. However, [fitting a curve](https://en.wikipedia.org/wiki/Curve_fitting "Curve fitting") and subtracting the fitted values from the original data can also be used in the context of Box–Jenkins models.

#### Seasonal differencing\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=7 "Edit section: Seasonal differencing")\]

At the model identification stage, the goal is to detect seasonality, if it exists, and to identify the order for the seasonal autoregressive and seasonal moving average terms. For many series, the period is known and a single seasonality term is sufficient. For example, for monthly data one would typically include either a seasonal AR 12 term or a seasonal MA 12 term. For Box–Jenkins models, one does not explicitly remove seasonality before fitting the model. Instead, one includes the order of the seasonal terms in the model specification to the [ARIMA](https://en.wikipedia.org/wiki/ARIMA "ARIMA") estimation software. However, it may be helpful to apply a seasonal difference to the data and regenerate the autocorrelation and partial autocorrelation plots. This may help in the model identification of the non-seasonal component of the model. In some cases, the seasonal differencing may remove most or all of the seasonality effect.

### Identify _p_ and _q_\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=8 "Edit section: Identify p and q")\]

Once stationarity and seasonality have been addressed, the next step is to identify the order (i.e. the _p_ and _q_) of the autoregressive and moving average terms. Different authors have different approaches for identifying _p_ and _q_. Brockwell and Davis (1991)[\[3\]](https://en.wikipedia.org/wiki/Box%E2%80%93Jenkins_method#cite_note-3) state "our prime criterion for model selection \[among ARMA(p,q) models\] will be the AICc", i.e. the [Akaike information criterion](https://en.wikipedia.org/wiki/Akaike_information_criterion "Akaike information criterion") with correction. Other authors use the autocorrelation plot and the partial autocorrelation plot, described below.

#### Autocorrelation and partial autocorrelation plots\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=9 "Edit section: Autocorrelation and partial autocorrelation plots")\]

The sample autocorrelation plot and the sample partial autocorrelation plot are compared to the theoretical behavior of these plots when the order is known.

Specifically, for an [AR(1)](https://en.wikipedia.org/wiki/AR(1) "AR(1)") process, the sample autocorrelation function should have an exponentially decreasing appearance. However, higher-order AR processes are often a mixture of exponentially decreasing and damped sinusoidal components.

For higher-order autoregressive processes, the sample autocorrelation needs to be supplemented with a partial autocorrelation plot. The partial autocorrelation of an AR(_p_) process becomes zero at lag _p_ + 1 and greater, so we examine the sample partial autocorrelation function to see if there is evidence of a departure from zero. This is usually determined by placing a 95% [confidence interval](https://en.wikipedia.org/wiki/Confidence_interval "Confidence interval") on the sample partial autocorrelation plot (most software programs that generate sample autocorrelation plots also plot this confidence interval). If the software program does not generate the confidence band, it is approximately ![\pm 2/{\sqrt {N}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/066f521b8d0e9aca5613399293d4db74c4b61501), with _N_ denoting the sample size.

The autocorrelation function of a [MA(_q_)](https://en.wikipedia.org/wiki/Moving_average_model "Moving average model") process becomes zero at lag _q_ + 1 and greater, so we examine the sample autocorrelation function to see where it essentially becomes zero. We do this by placing the 95% confidence interval for the sample autocorrelation function on the sample autocorrelation plot. Most software that can generate the autocorrelation plot can also generate this confidence interval.

The sample partial autocorrelation function is generally not helpful for identifying the order of the moving average process.

The following table summarizes how one can use the sample [autocorrelation function](https://en.wikipedia.org/wiki/Autocorrelation_function "Autocorrelation function") for model identification.

Shape

Indicated Model

Exponential, decaying to zero

[Autoregressive model](https://en.wikipedia.org/wiki/Autoregressive_model "Autoregressive model"). Use the partial autocorrelation plot to identify the order of the autoregressive model.

Alternating positive and negative, decaying to zero

Autoregressive model. Use the partial autocorrelation plot to help identify the order.

One or more spikes, rest are essentially zero (or close to zero)

[Moving average model](https://en.wikipedia.org/wiki/Moving_average_model "Moving average model"), order identified by where plot becomes zero.

Decay, starting after a few lags

Mixed autoregressive and moving average ([ARMA](https://en.wikipedia.org/wiki/Autoregressive_moving_average_model "Autoregressive moving average model")) model.

All zero or close to zero

Data are essentially random.

High values at fixed intervals

Include seasonal autoregressive term.

No decay to zero (or it decays extremely slowly)

Series is not stationary.

Hyndman & Athanasopoulos suggest the following:[\[4\]](https://en.wikipedia.org/wiki/Box%E2%80%93Jenkins_method#cite_note-4)

The data may follow an ARIMA(_p_,_d_,0) model if the ACF and PACF plots of the differenced data show the following patterns:

-   the ACF is exponentially decaying or sinusoidal;
-   there is a significant spike at lag _p_ in PACF, but none beyond lag _p_.

The data may follow an ARIMA(0,_d_,_q_) model if the ACF and PACF plots of the differenced data show the following patterns:

-   the PACF is exponentially decaying or sinusoidal;
-   there is a significant spike at lag _q_ in ACF, but none beyond lag _q_.

In practice, the sample autocorrelation and partial autocorrelation functions are [random variables](https://en.wikipedia.org/wiki/Random_variable "Random variable") and do not give the same picture as the theoretical functions. This makes the model identification more difficult. In particular, mixed models can be particularly difficult to identify. Although experience is helpful, developing good models using these sample plots can involve much trial and error.

## Box–Jenkins model estimation\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=10 "Edit section: Box–Jenkins model estimation")\]

Estimating the parameters for Box–Jenkins models involves numerically approximating the solutions of nonlinear equations. For this reason, it is common to use statistical software designed to handle to the approach – virtually all modern statistical packages feature this capability. The main approaches to fitting Box–Jenkins models are nonlinear least squares and maximum likelihood estimation. Maximum likelihood estimation is generally the preferred technique. The likelihood equations for the full Box–Jenkins model are complicated and are not included here. See (Brockwell and Davis, 1991) for the mathematical details.

## Box–Jenkins model diagnostics\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=11 "Edit section: Box–Jenkins model diagnostics")\]

### Assumptions for a stable univariate process\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=12 "Edit section: Assumptions for a stable univariate process")\]

Model diagnostics for Box–Jenkins models is similar to model validation for non-linear least squares fitting.

That is, the error term _At_ is assumed to follow the assumptions for a stationary univariate process. The residuals should be [white noise](https://en.wikipedia.org/wiki/White_noise "White noise") (or independent when their distributions are normal) drawings from a fixed distribution with a constant mean and variance. If the Box–Jenkins model is a good model for the data, the residuals should satisfy these assumptions.

If these assumptions are not satisfied, one needs to fit a more appropriate model. That is, go back to the model identification step and try to develop a better model. Hopefully the analysis of the residuals can provide some clues as to a more appropriate model.

One way to assess if the residuals from the Box–Jenkins model follow the assumptions is to generate [statistical graphics](https://en.wikipedia.org/wiki/Statistical_graphics "Statistical graphics") (including an autocorrelation plot) of the residuals. One could also look at the value of the [Box–Ljung statistic](https://en.wikipedia.org/wiki/Ljung%E2%80%93Box_test "Ljung–Box test").

## References\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=13 "Edit section: References")\]

## Further reading\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=14 "Edit section: Further reading")\]

-   Beveridge, S.; Oickle, C. (1994), "Comparison of Box–Jenkins and objective methods for determining the order of a non-seasonal ARMA model", _[Journal of Forecasting](https://en.wikipedia.org/wiki/Journal_of_Forecasting "Journal of Forecasting")_, **13**: 419–434, [doi](https://en.wikipedia.org/wiki/Doi_(identifier) "Doi (identifier)"):[10.1002/for.3980130502](https://doi.org/10.1002%2Ffor.3980130502)
-   Pankratz, Alan (1983), _Forecasting with Univariate Box–Jenkins Models: Concepts and Cases_, [John Wiley & Sons](https://en.wikipedia.org/wiki/John_Wiley_%26_Sons "John Wiley & Sons")

## External links\[[edit](https://en.wikipedia.org/w/index.php?title=Box%E2%80%93Jenkins_method&action=edit&section=15 "Edit section: External links")\]

-   [A First Course on Time Series Analysis](https://web.archive.org/web/20070318000551/http://statistik.mathematik.uni-wuerzburg.de/timeseries/) – an open source book on time series analysis with SAS (Chapter 7)
-   [Box–Jenkins models](http://www.itl.nist.gov/div898/handbook/pmc/section4/pmc445.htm) in the Engineering Statistics Handbook of [NIST](https://en.wikipedia.org/wiki/NIST "NIST")
-   [Box–Jenkins modelling](http://robjhyndman.com/papers/BoxJenkins.pdf) by Rob J Hyndman
-   [The Box–Jenkins methodology for time series models](http://support.sas.com/resources/papers/proceedings13/454-2013.pdf) by Theresa Hoang Diem Ngo

![Public Domain](https://upload.wikimedia.org/wikipedia/en/thumb/6/62/PD-icon.svg/12px-PD-icon.svg.png) This article incorporates [public domain material](https://en.wikipedia.org/wiki/Copyright_status_of_works_by_the_federal_government_of_the_United_States "Copyright status of works by the federal government of the United States") from the [National Institute of Standards and Technology](https://en.wikipedia.org/wiki/National_Institute_of_Standards_and_Technology "National Institute of Standards and Technology") website [https://www.nist.gov](https://www.nist.gov/).