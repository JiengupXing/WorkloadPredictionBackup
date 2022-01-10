# Autoregressive integrated moving average

"ARIMA" redirects here. Not to be confused with [Arimaa](https://en.wikipedia.org/wiki/Arimaa "Arimaa").

In [statistics](https://en.wikipedia.org/wiki/Statistics "Statistics") and [econometrics](https://en.wikipedia.org/wiki/Econometrics "Econometrics"), and in particular in [time series analysis](https://en.wikipedia.org/wiki/Time_series_analysis "Time series analysis"), an **autoregressive integrated moving average** (**ARIMA**) [model](https://en.wikipedia.org/wiki/Mathematical_model "Mathematical model") is a generalization of an [autoregressive moving average](https://en.wikipedia.org/wiki/Autoregressive_moving_average "Autoregressive moving average") (ARMA) model. Both of these models are fitted to [time series](https://en.wikipedia.org/wiki/Time_series "Time series") data either to better understand the data or to predict future points in the series ([forecasting](https://en.wikipedia.org/wiki/Forecasting "Forecasting")). ARIMA models are applied in some cases where data show evidence of [non-stationarity](https://en.wikipedia.org/wiki/Stationary_process "Stationary process") in the sense of mean (but not variance/[autocovariance](https://en.wikipedia.org/wiki/Autocovariance "Autocovariance")), where an initial differencing step (corresponding to the ["integrated"](https://en.wikipedia.org/wiki/Order_of_integration "Order of integration") part of the model) can be applied one or more times to eliminate the non-stationarity of the mean function (i.e., the trend).[\[1\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-1) When the seasonality shows in a time series, the seasonal-differencing[\[2\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:1-2) could be applied to eliminate the seasonal component. Since the [ARMA](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model "Autoregressive–moving-average model") model, according to the Wold's decomposition theorem,[\[3\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-3)[\[4\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:5-4)[\[5\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:4-5) is theoretically sufficient to describe a **regular** (a.k.a. purely nondeterministic[\[5\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:4-5)) [wide-sense stationary](https://en.wikipedia.org/wiki/Wide-sense_stationary "Wide-sense stationary") time series, we are motivated to make stationary a non-stationary time series, e.g., by using differencing, before we can use the [ARMA](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model "Autoregressive–moving-average model") model.[\[6\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:2-6) Note that if the time series contains a **predictable** sub-process (a.k.a. pure sine or complex-valued exponential process[\[4\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:5-4)), the predictable component is treated as a non-zero-mean but periodic (i.e., seasonal) component in the ARIMA framework so that it is eliminated by the seasonal differencing.

The AR part of ARIMA indicates that the evolving variable of interest is [regressed](https://en.wikipedia.org/wiki/Linear_regression "Linear regression") on its own lagged (i.e., prior) values. The MA part indicates that the [regression error](https://en.wikipedia.org/wiki/Errors_and_residuals_in_statistics "Errors and residuals in statistics") is actually a [linear combination](https://en.wikipedia.org/wiki/Linear_combination "Linear combination") of error terms whose values occurred contemporaneously and at various times in the past.[\[7\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-7) The I (for "integrated") indicates that the data values have been replaced with the difference between their values and the previous values (and this differencing process may have been performed more than once). The purpose of each of these features is to make the model fit the data as well as possible.

Non-seasonal ARIMA models are generally denoted ARIMA(_p_,_d_,_q_) where [parameters](https://en.wikipedia.org/wiki/Parameter "Parameter") _p_, _d_, and _q_ are non-negative integers, _p_ is the order (number of time lags) of the [autoregressive model](https://en.wikipedia.org/wiki/Autoregressive_model "Autoregressive model"), _d_ is the degree of differencing (the number of times the data have had past values subtracted), and _q_ is the order of the [moving-average model](https://en.wikipedia.org/wiki/Moving-average_model "Moving-average model"). Seasonal ARIMA models are usually denoted ARIMA(_p_,_d_,_q_)(_P_,_D_,_Q_)_m_, where _m_ refers to the number of periods in each season, and the uppercase _P_,_D_,_Q_ refer to the autoregressive, differencing, and moving average terms for the seasonal part of the ARIMA model.[\[8\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-8)[\[2\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:1-2)

When two out of the three terms are zeros, the model may be referred to based on the non-zero parameter, dropping "AR", "I" or "MA" from the acronym describing the model. For example, ![{\displaystyle {\text{ARIMA}}(1,0,0)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5db460c9aef01d9ac24615eddae93e270cfa7e84) is AR(1), ![{\displaystyle {\text{ARIMA}}(0,1,0)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8d1b5adfd1e94011dcd971b07f61b749bd13da0b) is I(1), and ![{\displaystyle {\text{ARIMA}}(0,0,1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/14af3af7ab5a90ca622531f0b2168f1a09442284) is MA(1).

ARIMA models can be estimated following the [Box–Jenkins](https://en.wikipedia.org/wiki/Box%E2%80%93Jenkins_method "Box–Jenkins method") approach.

## Definition\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=1 "Edit section: Definition")\]

Given time series data _X__t_ where _t_ is an integer index and the _X__t_ are real numbers, an ![{\displaystyle {\text{ARMA}}(p',q)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9388d4352d859146c1d1310ba76fd91323830ff6) model is given by

![{\displaystyle X_{t}-\alpha _{1}X_{t-1}-\dots -\alpha _{p'}X_{t-p'}=\varepsilon _{t}+\theta _{1}\varepsilon _{t-1}+\cdots +\theta _{q}\varepsilon _{t-q},}](https://wikimedia.org/api/rest_v1/media/math/render/svg/433c765f004fe1138737630568375a41f4e4d659)

or equivalently by

![\left(1-\sum _{i=1}^{p'}\alpha _{i}L^{i}\right)X_{t}=\left(1+\sum _{i=1}^{q}\theta _{i}L^{i}\right)\varepsilon _{t}\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/1d1c4e1959722b56ce5e5841b9dc3167ec9072b3)

where ![L](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) is the [lag operator](https://en.wikipedia.org/wiki/Lag_operator "Lag operator"), the ![\alpha _{i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3b1fb627423abe4988b7ed88d4920bf1ec074790) are the parameters of the autoregressive part of the model, the ![\theta _{i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/302b19204ed378e99ff4575341a67eebdbe5a555) are the parameters of the moving average part and the ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a) are error terms. The error terms ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a) are generally assumed to be [independent, identically distributed](https://en.wikipedia.org/wiki/Independent_and_identically-distributed_random_variables "Independent and identically-distributed random variables") variables sampled from a [normal distribution](https://en.wikipedia.org/wiki/Normal_distribution "Normal distribution") with zero mean.

Assume now that the polynomial ![{\displaystyle \textstyle \left(1-\sum _{i=1}^{p'}\alpha _{i}L^{i}\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f486c00c5614d866ea8d945a05b49a12ed6af2c8) has a [unit root](https://en.wikipedia.org/wiki/Unit_root "Unit root") (a factor ![{\displaystyle (1-L)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ca80398d27a2799114a84401998708b0657183a5)) of multiplicity _d_. Then it can be rewritten as:

![{\displaystyle \left(1-\sum _{i=1}^{p'}\alpha _{i}L^{i}\right)=\left(1-\sum _{i=1}^{p'-d}\varphi _{i}L^{i}\right)\left(1-L\right)^{d}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2de36b8a5900685564e79820d2af9c2864364cf5)

An ARIMA(_p_,_d_,_q_) process expresses this polynomial factorisation property with _p_\=_p'−d_, and is given by:

![{\displaystyle \left(1-\sum _{i=1}^{p}\varphi _{i}L^{i}\right)(1-L)^{d}X_{t}=\left(1+\sum _{i=1}^{q}\theta _{i}L^{i}\right)\varepsilon _{t}\,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/12cc5e99bc1595494ef8219d70b304784e3933d0)

and thus can be thought as a particular case of an ARMA(_p+d_,_q_) process having the autoregressive polynomial with _d_ unit roots. (For this reason, no process that is accurately described by an ARIMA model with _d_ > 0 is [wide-sense stationary](https://en.wikipedia.org/wiki/Wide-sense_stationary "Wide-sense stationary").)

The above can be generalized as follows.

![{\displaystyle \left(1-\sum _{i=1}^{p}\varphi _{i}L^{i}\right)(1-L)^{d}X_{t}=\delta +\left(1+\sum _{i=1}^{q}\theta _{i}L^{i}\right)\varepsilon _{t}.\,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b6ebbe31d07e994b209c391e3d6f8f5d88e267c3)

This defines an ARIMA(_p_,_d_,_q_) process with **drift** ![{\displaystyle {\frac {\delta }{1-\sum \varphi _{i}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8adcd4910234210e3e435f871e780dddd78dc642).

## Other special forms\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=2 "Edit section: Other special forms")\]

The explicit identification of the factorisation of the autoregression polynomial into factors as above, can be extended to other cases, firstly to apply to the moving average polynomial and secondly to include other special factors. For example, having a factor ![{\displaystyle (1-L^{s})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ba22d1c2f97b1966b45a280a9e8ae3621ba7d874) in a model is one way of including a non-stationary seasonality of period _s_ into the model; this factor has the effect of re-expressing the data as changes from _s_ periods ago. Another example is the factor ![\left(1-{\sqrt {3}}L+L^{2}\right)](https://wikimedia.org/api/rest_v1/media/math/render/svg/26e3890d84d3e234fdc9c026d583c0a25b981741), which includes a (non-stationary) seasonality of period 2.\[_[clarification needed](https://en.wikipedia.org/wiki/Wikipedia:Please_clarify "Wikipedia:Please clarify")_\] The effect of the first type of factor is to allow each season's value to drift separately over time, whereas with the second type values for adjacent seasons move together.\[_[clarification needed](https://en.wikipedia.org/wiki/Wikipedia:Please_clarify "Wikipedia:Please clarify")_\]

Identification and specification of appropriate factors in an ARIMA model can be an important step in modelling as it can allow a reduction in the overall number of parameters to be estimated, while allowing the imposition on the model of types of behaviour that logic and experience suggest should be there.

## Differencing\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=3 "Edit section: Differencing")\]

"Differencing" redirects here. For other uses, see [Difference](https://en.wikipedia.org/wiki/Difference_(disambiguation) "Difference (disambiguation)").

A stationary time series's properties do not depend on the time at which the series is observed. Specifically, for a [wide-sense stationary](https://en.wikipedia.org/wiki/Wide-sense_stationary "Wide-sense stationary") time series, the mean and the variance/[autocovariance](https://en.wikipedia.org/wiki/Autocovariance "Autocovariance") keep constant over time. **Differencing** in statistics is a transformation applied to a non-stationary time-series in order to make it stationary _in the mean sense_ (viz., to remove the non-constant trend), but having nothing to do with the non-stationarity of the variance or [autocovariance](https://en.wikipedia.org/wiki/Autocovariance "Autocovariance"). Likewise, the **seasonal differencing** is applied to a seasonal time-series to remove the seasonal component. From the perspective of signal processing, especially the [Fourier spectral analysis](https://en.wikipedia.org/wiki/Fourier_analysis "Fourier analysis") theory, the trend is the low-frequency part in the spectrum of a non-stationary time series, while the season is the periodic-frequency part in the spectrum of it. Therefore, the differencing works as a [high-pass](https://en.wikipedia.org/wiki/High-pass_filter "High-pass filter") (i.e., low-stop) filter and the seasonal-differencing as a [comb filter](https://en.wikipedia.org/wiki/Comb_filter "Comb filter") to suppress the low-frequency trend and the periodic-frequency season in the spectrum domain (rather than directly in the time domain), respectively.[\[6\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:2-6) This perspective explains the philosophy, mathematics, power, and drawbacks of the differencing and seasonal differencing.

To difference the data, the difference between consecutive observations is computed. Mathematically, this is shown as

![{\displaystyle y_{t}'=y_{t}-y_{t-1}\,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d0d29193070515cbacc44e9f2e2d4c4ec69ec685)

Differencing removes the changes in the level of a time series, eliminating trend and seasonality and consequently stabilizing the mean of the time series.[\[6\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:2-6)

Sometimes it may be necessary to difference the data a second time to obtain a stationary time series, which is referred to as **second-order differencing**:

![{\displaystyle {\begin{aligned}y_{t}^{*}&=y_{t}'-y_{t-1}'\\&=(y_{t}-y_{t-1})-(y_{t-1}-y_{t-2})\\&=y_{t}-2y_{t-1}+y_{t-2}\end{aligned}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e83f9ed5de7d6f2d61f3b346363cf2c4282dc0f)

Another method of differencing data is seasonal differencing, which involves computing the difference between an observation and the corresponding observation in the previous season e.g a year. This is shown as:

![{\displaystyle y_{t}'=y_{t}-y_{t-m}\quad {\text{where }}m={\text{duration of season}}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c234880f612d5324c31cfb502111ca7d858715ef)

The differenced data are then used for the estimation of an [ARMA](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model "Autoregressive–moving-average model") model.

## Examples\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=4 "Edit section: Examples")\]

Some well-known special cases arise naturally or are mathematically equivalent to other popular forecasting models. For example:

-   An ARIMA(0, 1, 0) model (or I(1) model) is given by ![X_{t}=X_{t-1}+\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ef7031afecaf18292758c680255685f0c2aaf4cf) — which is simply a [random walk](https://en.wikipedia.org/wiki/Random_walk "Random walk").
-   An ARIMA(0, 1, 0) with a constant, given by ![X_{t}=c+X_{t-1}+\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/061b903cbf57ceb58e871ccdb3bd54e32ecbaf25) — which is a random walk with drift.
-   An ARIMA(0, 0, 0) model is a [white noise](https://en.wikipedia.org/wiki/White_noise "White noise") model.
-   An ARIMA(0, 1, 2) model is a Damped Holt's model.
-   An ARIMA(0, 1, 1) model without constant is a [basic exponential smoothing](https://en.wikipedia.org/wiki/Exponential_smoothing#Basic_(simple)_exponential_smoothing_(Holt_linear) "Exponential smoothing") model.[\[9\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:0-9)
-   An ARIMA(0, 2, 2) model is given by ![{\displaystyle X_{t}=2X_{t-1}-X_{t-2}+(\alpha +\beta -2)\varepsilon _{t-1}+(1-\alpha )\varepsilon _{t-2}+\varepsilon _{t}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ed3d221889c6e7c0ae72d551292e69af0c0957ea) — which is equivalent to Holt's linear method with additive errors, or [double exponential smoothing](https://en.wikipedia.org/wiki/Exponential_smoothing#Double_exponential_smoothing "Exponential smoothing").[\[9\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:0-9)

## Choosing the order\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=5 "Edit section: Choosing the order")\]

The order p and q can be determined using the sample autocorrelation function (ACF), partial autocorrelation function (PACF), and/or extended autocorrelation function (EACF) method.[\[10\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:3-10)

Other alternative methods include AIC, BIC, etc.[\[10\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-:3-10) To determine the order of a non-seasonal ARIMA model, a useful criterion is the [Akaike information criterion (AIC)](https://en.wikipedia.org/wiki/Akaike_information_criterion "Akaike information criterion"). It is written as

![{\displaystyle {\text{AIC}}=-2\log(L)+2(p+q+k),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ecb55c0f99fe92fafb85c8edb7cfefa2c5bec6b2)

where _L_ is the likelihood of the data, _p_ is the order of the autoregressive part and _q_ is the order of the moving average part. The _k_ represents the intercept of the ARIMA model. For AIC, if _k_ = 1 then there is an intercept in the ARIMA model (_c_ ≠ 0) and if _k_ \= 0 then there is no intercept in the ARIMA model (_c_ \= 0).

The corrected AIC for ARIMA models can be written as

![{\displaystyle {\text{AICc}}={\text{AIC}}+{\frac {2(p+q+k)(p+q+k+1)}{T-p-q-k-1}}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/542763ffd774cf9296c11f21af1bd7fbdd171c96)

The [Bayesian Information Criterion (BIC)](https://en.wikipedia.org/wiki/Bayesian_information_criterion "Bayesian information criterion") can be written as

![{\displaystyle {\text{BIC}}={\text{AIC}}+((\log T)-2)(p+q+k).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/754009508fb0a5ec4516c80c204345fbbd9b97de)

The objective is to minimize the AIC, AICc or BIC values for a good model. The lower the value of one of these criteria for a range of models being investigated, the better the model will suit the data. The AIC and the BIC are used for two completely different purposes. While the AIC tries to approximate models towards the reality of the situation, the BIC attempts to find the perfect fit. The BIC approach is often criticized as there never is a perfect fit to real-life complex data; however, it is still a useful method for selection as it penalizes models more heavily for having more parameters than the AIC would.

AICc can only be used to compare ARIMA models with the same orders of differencing. For ARIMAs with different orders of differencing, [RMSE](https://en.wikipedia.org/wiki/Root-mean-square_deviation "Root-mean-square deviation") can be used for model comparison.

## Estimation of coefficients\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=6 "Edit section: Estimation of coefficients")\]

[![[icon]](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1c/Wiki_letter_w_cropped.svg/20px-Wiki_letter_w_cropped.svg.png)](https://en.wikipedia.org/wiki/File:Wiki_letter_w_cropped.svg)

**This section is empty.** You can help by [adding to it](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=). _(March 2017)_

## Forecasts using ARIMA models\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=7 "Edit section: Forecasts using ARIMA models")\]

The ARIMA model can be viewed as a "cascade" of two models. The first is non-stationary:

![{\displaystyle Y_{t}=(1-L)^{d}X_{t}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c60f26acd2fabca6d27cf919cbab419b46882f56)

while the second is [wide-sense stationary](https://en.wikipedia.org/wiki/Wide-sense_stationary "Wide-sense stationary"):

![{\displaystyle \left(1-\sum _{i=1}^{p}\varphi _{i}L^{i}\right)Y_{t}=\left(1+\sum _{i=1}^{q}\theta _{i}L^{i}\right)\varepsilon _{t}\,.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d5d1869a63c7037823a5f2d34c78e5261b1f59d5)

Now forecasts can be made for the process ![Y_{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/95734a78eb8407939c3496cbfd92763ced1e41e1), using a generalization of the method of [autoregressive forecasting](https://en.wikipedia.org/wiki/Autoregressive_model#n-step-ahead_forecasting "Autoregressive model").

### Forecast intervals\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=8 "Edit section: Forecast intervals")\]

The forecast intervals ([confidence intervals](https://en.wikipedia.org/wiki/Confidence_interval "Confidence interval") for forecasts) for ARIMA models are based on assumptions that the residuals are uncorrelated and normally distributed. If either of these assumptions does not hold, then the forecast intervals may be incorrect. For this reason, researchers plot the ACF and histogram of the residuals to check the assumptions before producing forecast intervals.

95% forecast interval: ![{\displaystyle {\hat {y}}_{T+h\,\mid \,T}\pm 1.96{\sqrt {v_{T+h\,\mid \,T}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/25474c8f2cea5cf2849bb708c636e330c8a292fb), where ![{\displaystyle v_{T+h\mid T}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d3e015fc53947e5e4d509add0219e28e257ee4ee) is the variance of ![{\displaystyle y_{T+h}\mid y_{1},\dots ,y_{T}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a22a2aade63b27c220d45320eea34c54561ccd38).

For ![h=1](https://wikimedia.org/api/rest_v1/media/math/render/svg/3d5d82ae0a834e0d0b839e2ea7a0f8eac0ee791d), ![{\displaystyle v_{T+h\,\mid \,T}={\hat {\sigma }}^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6b60ab98ba3b9f7ea6f583c118c4735f17c320d1) for all ARIMA models regardless of parameters and orders.

For ARIMA(0,0,q), ![{\displaystyle y_{t}=e_{t}+\sum _{i=1}^{q}\theta _{i}e_{t-i}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b513defcec9059a152cfcb1265c03c853ae53c88)

![{\displaystyle v_{T+h\,\mid \,T}={\hat {\sigma }}^{2}\left[1+\sum _{i=1}^{h-1}\theta _{i}e_{t-i}\right],{\text{ for }}h=2,3,\ldots }](https://wikimedia.org/api/rest_v1/media/math/render/svg/df81646fa3a54be8b01e68422525ddcfc7d33e5c)\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

In general, forecast intervals from ARIMA models will increase as the forecast horizon increases.

## Variations and extensions\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=9 "Edit section: Variations and extensions")\]

A number of variations on the ARIMA model are commonly employed. If multiple time series are used then the ![X_{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/82120d04dfb3cbadc4912951dd12b5568c9cd8f3) can be thought of as vectors and a VARIMA model may be appropriate. Sometimes a seasonal effect is suspected in the model; in that case, it is generally considered better to use a SARIMA (seasonal ARIMA) model than to increase the order of the AR or MA parts of the model.[\[11\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-ARIMAKHORDHA2018-11) If the time-series is suspected to exhibit [long-range dependence](https://en.wikipedia.org/wiki/Long-range_dependence "Long-range dependence"), then the _d_ parameter may be allowed to have non-integer values in an [autoregressive fractionally integrated moving average](https://en.wikipedia.org/wiki/Autoregressive_fractionally_integrated_moving_average "Autoregressive fractionally integrated moving average") model, which is also called a Fractional ARIMA (FARIMA or ARFIMA) model.

## Software implementations\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=10 "Edit section: Software implementations")\]

Various packages that apply methodology like [Box–Jenkins](https://en.wikipedia.org/wiki/Box%E2%80%93Jenkins_method "Box–Jenkins method") parameter optimization are available to find the right parameters for the ARIMA model.

-   [EViews](https://en.wikipedia.org/wiki/EViews "EViews"): has extensive ARIMA and SARIMA capabilities.
-   [Julia](https://en.wikipedia.org/wiki/Julia_language "Julia language"): contains an ARIMA implementation in the TimeModels package[\[12\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-12)
-   [Mathematica](https://en.wikipedia.org/wiki/Mathematica "Mathematica"): includes [ARIMAProcess](http://reference.wolfram.com/mathematica/ref/ARIMAProcess.html) function.
-   [MATLAB](https://en.wikipedia.org/wiki/MATLAB "MATLAB"): the [Econometrics Toolbox](http://www.mathworks.com/products/econometrics/) includes [ARIMA models](http://www.mathworks.com/help/econ/arimaclass.html) and [regression with ARIMA errors](http://www.mathworks.com/help/econ/regarimaclass.html)
-   [NCSS](https://en.wikipedia.org/wiki/NCSS_(statistical_software) "NCSS (statistical software)"): includes several procedures for `ARIMA` fitting and forecasting.[\[13\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-13)[\[14\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-14)[\[15\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-15)
-   [Python](https://en.wikipedia.org/wiki/Python_(programming_language) "Python (programming language)"): the ["statsmodels"](https://www.statsmodels.org/) package includes models for time series analysis – univariate time series analysis: AR, ARIMA – vector autoregressive models, VAR and structural VAR – descriptive statistics and process models for time series analysis.
-   [R](https://en.wikipedia.org/wiki/R_(programming_language) "R (programming language)"): the standard R _stats_ package includes an _arima_ function, which is documented in ["ARIMA Modelling of Time Series"](http://search.r-project.org/R/library/stats/html/arima.html). Besides the ![{\displaystyle {\text{ARIMA}}(p,d,q)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/220bf9e73e19643023fec004310cf8c82a41e47f) part, the function also includes seasonal factors, an intercept term, and exogenous variables (_xreg_, called "external regressors"). The CRAN task view on [Time Series](https://cran.r-project.org/web/views/TimeSeries.html) is the reference with many more links. The ["forecast"](https://cran.r-project.org/web/packages/forecast/index.html) package in [R](https://en.wikipedia.org/wiki/R_(programming_language) "R (programming language)") can automatically select an ARIMA model for a given time series with the `auto.arima()` function and can also simulate seasonal and non-seasonal ARIMA models with its `simulate.Arima()` function.[\[16\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-16)
-   [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language) "Ruby (programming language)"): the ["statsample-timeseries"](https://rubygems.org/gems/statsample-timeseries) gem is used for time series analysis, including ARIMA models and Kalman Filtering.
-   [JavaScript](https://en.wikipedia.org/wiki/JavaScript "JavaScript"): the ["arima"](https://www.npmjs.com/package/arima) package includes models for time series analysis and forecasting (ARIMA, SARIMA, SARIMAX, AutoARIMA)
-   [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)"): the ["ctsa"](https://github.com/rafat/ctsa/) package includes ARIMA, SARIMA, SARIMAX, AutoARIMA and multiple methods for time series analysis.
-   [SAFE TOOLBOXES](http://www.safetoolboxes.com/): includes [ARIMA modelling](http://www.safetoolboxes.com/howto_fitarimamodel.html) and [regression with ARIMA errors](http://www.safetoolboxes.com/howto_transformtimeseries.html).
-   [SAS](https://en.wikipedia.org/wiki/SAS_(software) "SAS (software)"): includes extensive ARIMA processing in its Econometric and Time Series Analysis system: SAS/ETS.
-   IBM [SPSS](https://en.wikipedia.org/wiki/SPSS "SPSS"): includes ARIMA modeling in its Statistics and Modeler statistical packages. The default Expert Modeler feature evaluates a range of seasonal and non-seasonal autoregressive (_p_), integrated (_d_), and moving average (_q_) settings and seven exponential smoothing models. The Expert Modeler can also transform the target time-series data into its square root or natural log. The user also has the option to restrict the Expert Modeler to ARIMA models, or to manually enter ARIMA nonseasonal and seasonal _p_, _d_, and _q_ settings without Expert Modeler. Automatic outlier detection is available for seven types of outliers, and the detected outliers will be accommodated in the time-series model if this feature is selected.
-   [SAP](https://en.wikipedia.org/wiki/SAP_AG "SAP AG"): the APO-FCS package[\[17\]](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_note-17) in [SAP ERP](https://en.wikipedia.org/wiki/SAP_ERP "SAP ERP") from [SAP](https://en.wikipedia.org/wiki/SAP_AG "SAP AG") allows creation and fitting of ARIMA models using the Box–Jenkins methodology.
-   [SQL Server Analysis Services](https://en.wikipedia.org/wiki/SQL_Server_Analysis_Services "SQL Server Analysis Services"): from [Microsoft](https://en.wikipedia.org/wiki/Microsoft "Microsoft") includes ARIMA as a Data Mining algorithm.
-   [Stata](https://en.wikipedia.org/wiki/Stata "Stata") includes ARIMA modelling (using its arima command) as of Stata 9.
-   [StatSim](https://statsim.com/): includes ARIMA models in the [Forecast](https://statsim.com/forecast/) web app.
-   [Teradata](https://en.wikipedia.org/wiki/Teradata "Teradata") Vantage has the ARIMA function as part of its machine learning engine.
-   TOL (Time Oriented Language) is designed to model ARIMA models (including SARIMA, ARIMAX and DSARIMAX variants) [\[1\]](https://web.archive.org/web/20170327171617/https://www.tol-project.org/).
-   [Scala](https://en.wikipedia.org/wiki/Scala_(programming_language) "Scala (programming language)"): [spark-timeseries](https://github.com/sryza/spark-timeseries) library contains ARIMA implementation for Scala, Java and Python. Implementation is designed to run on [Apache Spark](https://en.wikipedia.org/wiki/Apache_Spark "Apache Spark").
-   [PostgreSQL](https://en.wikipedia.org/wiki/PostgreSQL "PostgreSQL")/MadLib: [Time Series Analysis/ARIMA](https://madlib.apache.org/docs/latest/group__grp__arima.html).
-   [X-12-ARIMA](https://en.wikipedia.org/wiki/X-12-ARIMA "X-12-ARIMA"): from the [US Bureau of the Census](https://en.wikipedia.org/wiki/United_States_Census_Bureau "United States Census Bureau")

## See also\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=11 "Edit section: See also")\]

-   [Autocorrelation](https://en.wikipedia.org/wiki/Autocorrelation "Autocorrelation")
-   [ARMA](https://en.wikipedia.org/wiki/Autoregressive_moving_average_model "Autoregressive moving average model")
-   [Partial autocorrelation](https://en.wikipedia.org/wiki/Partial_autocorrelation "Partial autocorrelation")
-   [Finite impulse response](https://en.wikipedia.org/wiki/Finite_impulse_response "Finite impulse response")
-   [Infinite impulse response](https://en.wikipedia.org/wiki/Infinite_impulse_response "Infinite impulse response")

## References\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=12 "Edit section: References")\]

1.  **[^](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-1 "Jump up")** For further information on Stationarity and Differencing see [https://www.otexts.org/fpp/8/1](https://www.otexts.org/fpp/8/1)
2.  ^ [Jump up to: _**a**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:1_2-0) [_**b**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:1_2-1) Hyndman, Rob J; Athanasopoulos, George. [_8.9 Seasonal ARIMA models_](https://www.otexts.org/fpp/8/9). _Forecasting: principles and practice_. oTexts. Retrieved 19 May 2015.
3.  **[^](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-3 "Jump up")** Hamilton, James (1994). _Time Series Analysis_. Princeton University Press. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [9780691042893](https://en.wikipedia.org/wiki/Special:BookSources/9780691042893 "Special:BookSources/9780691042893").
4.  ^ [Jump up to: _**a**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:5_4-0) [_**b**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:5_4-1) Papoulis, Athanasios (2002). _Probability, Random Variables, and Stochastic processes_. Tata McGraw-Hill Education.
5.  ^ [Jump up to: _**a**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:4_5-0) [_**b**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:4_5-1) Triacca, Umberto (19 Feb 2021). ["The Wold Decomposition Theorem"](http://www.phdeconomics.sssup.it/documents/Lesson11.pdf) (PDF).
6.  ^ [Jump up to: _**a**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:2_6-0) [_**b**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:2_6-1) [_**c**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:2_6-2) Wang, Shixiong; Li, Chongshou; Lim, Andrew (2019-12-18). "Why Are the ARIMA and SARIMA not Sufficient". [arXiv](https://en.wikipedia.org/wiki/ArXiv_(identifier) "ArXiv (identifier)"):[1904.07632](https://arxiv.org/abs/1904.07632) \[[stat.AP](https://arxiv.org/archive/stat.AP)\].
7.  **[^](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-7 "Jump up")** Box, George E. P. (2015). _Time Series Analysis: Forecasting and Control_. WILEY. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [978-1-118-67502-1](https://en.wikipedia.org/wiki/Special:BookSources/978-1-118-67502-1 "Special:BookSources/978-1-118-67502-1").
8.  **[^](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-8 "Jump up")** ["Notation for ARIMA Models"](https://support.sas.com/documentation/cdl/en/etsug/63939/HTML/default/viewer.htm#etsug_tffordet_sect016.htm). _Time Series Forecasting System_. SAS Institute. Retrieved 19 May 2015.
9.  ^ [Jump up to: _**a**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:0_9-0) [_**b**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:0_9-1) ["Introduction to ARIMA models"](http://people.duke.edu/~rnau/411arim.htm#arima010). _people.duke.edu_. Retrieved 2016-06-05.
10.  ^ [Jump up to: _**a**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:3_10-0) [_**b**_](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-:3_10-1) Missouri State University. ["Model Specification, Time Series Analysis"](http://people.missouristate.edu/songfengzheng/Teaching/MTH548/Time%20Series-ch06.pdf) (PDF).
11.  **[^](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-ARIMAKHORDHA2018_11-0 "Jump up")** Swain, S; et al. (2018). "Development of an ARIMA Model for Monthly Rainfall Forecasting over Khordha District, Odisha, India". _Recent Findings in Intelligent Computing Techniques_. _Recent Findings in Intelligent Computing Techniques (Advances in Intelligent Systems and Computing_. Advances in Intelligent Systems and Computing. **708**. pp. 325–331). [doi](https://en.wikipedia.org/wiki/Doi_(identifier) "Doi (identifier)"):[10.1007/978-981-10-8636-6\_34](https://doi.org/10.1007%2F978-981-10-8636-6_34). [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [978-981-10-8635-9](https://en.wikipedia.org/wiki/Special:BookSources/978-981-10-8635-9 "Special:BookSources/978-981-10-8635-9").
12.  **[^](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-12 "Jump up")** [TimeModels.jl](https://github.com/JuliaStats/TimeModels.jl) www.github.com
13.  **[^](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-13 "Jump up")** [ARIMA in NCSS](http://ncss.wpengine.netdna-cdn.com/wp-content/themes/ncss/pdf/Procedures/NCSS/ARIMA-Box-Jenkins.pdf),
14.  **[^](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-14 "Jump up")** [Automatic ARMA in NCSS](http://ncss.wpengine.netdna-cdn.com/wp-content/themes/ncss/pdf/Procedures/NCSS/Automatic_ARMA.pdf),
15.  **[^](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-15 "Jump up")** [Autocorrelations and Partial Autocorrelations in NCSS](http://ncss.wpengine.netdna-cdn.com/wp-content/themes/ncss/pdf/Procedures/NCSS/Autocorrelations.pdf)
16.  **[^](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-16 "Jump up")** [_8.7 ARIMA modelling in R | OTexts_](https://www.otexts.org/fpp/8/7). _www.otexts.org_. Retrieved 2016-05-12.
17.  **[^](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average#cite_ref-17 "Jump up")** ["Box Jenkins model"](http://help.sap.com/saphelp_45b/helpdata/en/35/8a524b52060634e10000009b38f9b9/content.htm). SAP. Retrieved 8 March 2013.

## Further reading\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=13 "Edit section: Further reading")\]

-   Asteriou, Dimitros; Hall, Stephen G. (2011). "ARIMA Models and the Box–Jenkins Methodology". _Applied Econometrics_ (Second ed.). Palgrave MacMillan. pp. 265–286. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [978-0-230-27182-1](https://en.wikipedia.org/wiki/Special:BookSources/978-0-230-27182-1 "Special:BookSources/978-0-230-27182-1").
-   Mills, Terence C. (1990). [_Time Series Techniques for Economists_](https://archive.org/details/timeseriestechni0000mill). Cambridge University Press. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [978-0-521-34339-8](https://en.wikipedia.org/wiki/Special:BookSources/978-0-521-34339-8 "Special:BookSources/978-0-521-34339-8").
-   Percival, Donald B.; Walden, Andrew T. (1993). _Spectral Analysis for Physical Applications_. Cambridge University Press. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [978-0-521-35532-2](https://en.wikipedia.org/wiki/Special:BookSources/978-0-521-35532-2 "Special:BookSources/978-0-521-35532-2").

## External links\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_integrated_moving_average&action=edit&section=14 "Edit section: External links")\]

-   [The US Census Bureau uses ARIMA for "seasonally adjusted" data (programs, docs, and papers here)](https://web.archive.org/web/20160205235259/http://www.census.gov/srd/www/x12a/)
-   [Lecture notes on ARIMA models (Robert Nau, Duke University)](http://people.duke.edu/~rnau/411arim.htm)