# Autoregressive–moving-average model
In the [statistical](https://en.wikipedia.org/wiki/Statistics "Statistics") analysis of [time series](https://en.wikipedia.org/wiki/Time_series "Time series"), **autoregressive–moving-average** (**ARMA**) **models** provide a parsimonious description of a [(weakly) stationary stochastic process](https://en.wikipedia.org/wiki/Stationary_stochastic_process "Stationary stochastic process") in terms of two polynomials, one for the [autoregression](https://en.wikipedia.org/wiki/AR_model "AR model") (AR) and the second for the [moving average](https://en.wikipedia.org/wiki/MA_model "MA model") (MA). The general ARMA model was described in the 1951 thesis of [Peter Whittle](https://en.wikipedia.org/wiki/Peter_Whittle_(mathematician) "Peter Whittle (mathematician)"), _Hypothesis testing in time series analysis_, and it was popularized in the 1970 book by [George E. P. Box](https://en.wikipedia.org/wiki/George_E._P._Box "George E. P. Box") and [Gwilym Jenkins](https://en.wikipedia.org/wiki/Gwilym_Jenkins "Gwilym Jenkins").

Given a time series of data _X__t_ , the ARMA model is a tool for understanding and, perhaps, predicting future values in this series. The AR part involves regressing the variable on its own lagged (i.e., past) values. The MA part involves modeling the [error term](https://en.wikipedia.org/wiki/Errors_and_residuals_in_statistics "Errors and residuals in statistics") as a [linear combination](https://en.wikipedia.org/wiki/Linear_combination "Linear combination") of error terms occurring contemporaneously and at various times in the past. The model is usually referred to as the ARMA(_p_,_q_) model where _p_ is the order of the AR part and _q_ is the order of the MA part (as defined below).

ARMA models can be estimated by using the [Box–Jenkins method](https://en.wikipedia.org/wiki/Box%E2%80%93Jenkins_method "Box–Jenkins method").

## Autoregressive model\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=1 "Edit section: Autoregressive model")\]

The notation AR(_p_) refers to the autoregressive model of order _p_. The AR(_p_) model is written

![X_{t}=c+\sum _{i=1}^{p}\varphi _{i}X_{t-i}+\varepsilon _{t}.\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/7252143f217525cfbf556ff59ebafacf13e638cb)

where ![\varphi _{1},\ldots ,\varphi _{p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d4fdc81c8ea00ebabdeee779385a8e22e3c2b385) are [parameters](https://en.wikipedia.org/wiki/Parameter "Parameter"), ![c](https://wikimedia.org/api/rest_v1/media/math/render/svg/86a67b81c2de995bd608d5b2df50cd8cd7d92455) is a constant, and the random variable ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a) is [white noise](https://en.wikipedia.org/wiki/White_noise "White noise").

Some constraints are necessary on the values of the parameters so that the model remains [stationary](https://en.wikipedia.org/wiki/Stationary_process "Stationary process"). For example, processes in the AR(1) model with ![{\displaystyle |\varphi _{1}|\geq 1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5feb9de2fe8907d308f9eaaab3ff940d54b8fbf9) are not stationary.

## Moving-average model\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=2 "Edit section: Moving-average model")\]

The notation MA(_q_) refers to the moving average model of order _q_:

![X_{t}=\mu +\varepsilon _{t}+\sum _{i=1}^{q}\theta _{i}\varepsilon _{t-i}\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/233e2b4afeb090e821bd8f615b42f7b62269261e)

where the θ1, ..., θ_q_ are the parameters of the model, μ is the expectation of ![X_{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/82120d04dfb3cbadc4912951dd12b5568c9cd8f3) (often assumed to equal 0), and the ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a), ![\varepsilon _{t-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3a37a7842d23884524f98639ae682f2d1003b062),... are again, [white noise](https://en.wikipedia.org/wiki/White_noise "White noise") error terms.

## ARMA model\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=3 "Edit section: ARMA model")\]

The notation ARMA(_p_, _q_) refers to the model with _p_ autoregressive terms and _q_ moving-average terms. This model contains the AR(_p_) and MA(_q_) models,

![X_{t}=c+\varepsilon _{t}+\sum _{i=1}^{p}\varphi _{i}X_{t-i}+\sum _{i=1}^{q}\theta _{i}\varepsilon _{t-i}.\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/b03d4effdb520d36cc458ec5c2b231354d29d11a)

The general ARMA model was described in the 1951 thesis of [Peter Whittle](https://en.wikipedia.org/wiki/Peter_Whittle_(mathematician) "Peter Whittle (mathematician)"), who used mathematical analysis ([Laurent series](https://en.wikipedia.org/wiki/Laurent_series "Laurent series") and [Fourier analysis](https://en.wikipedia.org/wiki/Fourier_analysis "Fourier analysis")) and statistical inference.[\[1\]](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_note-1)[\[2\]](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_note-2) ARMA models were popularized by a 1970 book by [George E. P. Box](https://en.wikipedia.org/wiki/George_E._P._Box "George E. P. Box") and Jenkins, who expounded an iterative ([Box–Jenkins](https://en.wikipedia.org/wiki/Box%E2%80%93Jenkins "Box–Jenkins")) method for choosing and estimating them. This method was useful for low-order polynomials (of degree three or less).[\[3\]](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_note-3)

The ARMA model is essentially an [infinite impulse response](https://en.wikipedia.org/wiki/Infinite_impulse_response "Infinite impulse response") filter applied to white noise, with some additional interpretation placed on it.

## Note about the error terms\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=4 "Edit section: Note about the error terms")\]

The error terms ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a) are generally assumed to be [independent identically distributed random variables](https://en.wikipedia.org/wiki/Independent_identically_distributed_random_variables "Independent identically distributed random variables") (i.i.d.) sampled from a [normal distribution](https://en.wikipedia.org/wiki/Normal_distribution "Normal distribution") with zero mean: ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a) ~ N(0,σ2) where σ2 is the variance. These assumptions may be weakened but doing so will change the properties of the model. In particular, a change to the i.i.d. assumption would make a rather fundamental difference.

## Specification in terms of lag operator\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=5 "Edit section: Specification in terms of lag operator")\]

In some texts the models will be specified in terms of the [lag operator](https://en.wikipedia.org/wiki/Lag_operator "Lag operator") _L_. In these terms then the AR(_p_) model is given by

![\varepsilon _{t}=\left(1-\sum _{i=1}^{p}\varphi _{i}L^{i}\right)X_{t}=\varphi (L)X_{t}\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/6ef0ecbfbb781ca2cdbf8ade385a5e6f61c857be)

where ![\varphi ](https://wikimedia.org/api/rest_v1/media/math/render/svg/33ee699558d09cf9d653f6351f9fda0b2f4aaa3e) represents the polynomial

![\varphi (L)=1-\sum _{i=1}^{p}\varphi _{i}L^{i}.\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/e712f53fbf4578089aafea2da67501978b5d48d5)

The MA(_q_) model is given by

![X_{t}=\left(1+\sum _{i=1}^{q}\theta _{i}L^{i}\right)\varepsilon _{t}=\theta (L)\varepsilon _{t},\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/38f73b6ee628338328038af519ee087116785499)

where θ represents the polynomial

![\theta (L)=1+\sum _{i=1}^{q}\theta _{i}L^{i}.\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/2bcb382df680002b7ef1aedd733ca5a9923ac7fc)

Finally, the combined ARMA(_p_, _q_) model is given by

![\left(1-\sum _{i=1}^{p}\varphi _{i}L^{i}\right)X_{t}=\left(1+\sum _{i=1}^{q}\theta _{i}L^{i}\right)\varepsilon _{t}\,,](https://wikimedia.org/api/rest_v1/media/math/render/svg/b0563383c527751a556face903c7c8bcd84b79ea)

or more concisely,

![\varphi (L)X_{t}=\theta (L)\varepsilon _{t}\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/4e172b6df8cceca2b4dca9cab8101440591c5139)

or

![{\frac {\varphi (L)}{\theta (L)}}X_{t}=\varepsilon _{t}\,.](https://wikimedia.org/api/rest_v1/media/math/render/svg/cd64d10d7a2ef970c04008ded70eb2cbc7e7656a)

### Alternative notation\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=6 "Edit section: Alternative notation")\]

Some authors, including [Box](https://en.wikipedia.org/wiki/George_Box "George Box"), [Jenkins](https://en.wikipedia.org/wiki/Gwilym_M._Jenkins "Gwilym M. Jenkins") & Reinsel use a different convention for the autoregression coefficients.[\[4\]](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_note-4) This allows all the polynomials involving the lag operator to appear in a similar form throughout. Thus the ARMA model would be written as

![{\displaystyle \left(1-\sum _{i=1}^{p}\phi _{i}L^{i}\right)X_{t}=\left(1+\sum _{i=1}^{q}\theta _{i}L^{i}\right)\varepsilon _{t}\,.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ad0e1dcfb74156027002cc2294ffb1018d6a8219)

Moreover, starting summations from ![i=0](https://wikimedia.org/api/rest_v1/media/math/render/svg/31a682d568ee6a5fe51d76423186057f625ada5c) and setting ![{\displaystyle \phi _{0}=-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e5c82118f35a8d1ea9d8c2c41954599dec4139ad) and ![{\displaystyle \theta _{0}=1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9fa4f4d310f928fc441b2ea4fe5e26ddba8124a0), then we get an even more elegant formulation: ![{\displaystyle -\sum _{i=0}^{p}\phi _{i}L^{i}\;X_{t}=\sum _{i=0}^{q}\theta _{i}L^{i}\;\varepsilon _{t}\,.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1cabeb2aade0aec3442679bf6bd1269542f3a2b9)

## Fitting models\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=7 "Edit section: Fitting models")\]

### Choosing p and q\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=8 "Edit section: Choosing p and q")\]

Finding appropriate values of _p_ and _q_ in the ARMA(_p_,_q_) model can be facilitated by plotting the [partial autocorrelation functions](https://en.wikipedia.org/wiki/Partial_autocorrelation_function "Partial autocorrelation function") for an estimate of _p_, and likewise using the [autocorrelation functions](https://en.wikipedia.org/wiki/Autocorrelation_function "Autocorrelation function") for an estimate of _q_. Extended autocorrelation functions (EACF) can be used to simultaneously determine p and q.[\[5\]](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_note-5) Further information can be gleaned by considering the same functions for the residuals of a model fitted with an initial selection of _p_ and _q_.

Brockwell & Davis recommend using [Akaike information criterion](https://en.wikipedia.org/wiki/Akaike_information_criterion "Akaike information criterion") (AIC) for finding _p_ and _q_.[\[6\]](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_note-6) Another possible choice for order determining is the [BIC](https://en.wikipedia.org/wiki/Bayesian_information_criterion "Bayesian information criterion") criterion.

### Estimating coefficients\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=9 "Edit section: Estimating coefficients")\]

[![[icon]](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1c/Wiki_letter_w_cropped.svg/20px-Wiki_letter_w_cropped.svg.png)](https://en.wikipedia.org/wiki/File:Wiki_letter_w_cropped.svg)

This section **needs expansion**. You can help by [adding to it](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=). _(March 2017)_

ARMA models in general can be, after choosing _p_ and _q_, fitted by [least squares](https://en.wikipedia.org/wiki/Least_squares "Least squares") regression to find the values of the parameters which minimize the error term. It is generally considered good practice to find the smallest values of _p_ and _q_ which provide an acceptable fit to the data. For a pure AR model the [Yule-Walker equations](https://en.wikipedia.org/wiki/AR_model#Calculation_of_the_AR_parameters "AR model") may be used to provide a fit.

### Implementations in statistics packages\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=10 "Edit section: Implementations in statistics packages")\]

-   In [R](https://en.wikipedia.org/wiki/R_(programming_language) "R (programming language)"), the _arima_ function (in standard package _stats_) is documented in [ARIMA Modelling of Time Series](http://search.r-project.org/R/library/stats/html/arima.html). Extension packages contain related and extended functionality, e.g., the _tseries_ package includes an _arma_ function, documented in ["Fit ARMA Models to Time Series"](http://finzi.psych.upenn.edu/R/library/tseries/html/arma.html); the [_fracdiff_ package](https://cran.r-project.org/web/packages/fracdiff) contains _fracdiff()_ for fractionally integrated ARMA processes; and the [_forecast_ package](https://cran.r-project.org/web/packages/forecast/index.html) includes _auto.arima_ for selecting a parsimonious set of _p,q_. The CRAN task view on [Time Series](https://cran.r-project.org/web/views/TimeSeries.html) contains links to most of these.
-   [Mathematica](https://en.wikipedia.org/wiki/Mathematica "Mathematica") has a complete library of time series functions including ARMA.[\[7\]](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_note-7)
-   [MATLAB](https://en.wikipedia.org/wiki/MATLAB "MATLAB") includes functions such as [_arma_](http://www.mathworks.com/help/econ/arma-model.html) and [_ar_](http://www.mathworks.com/help/ident/ref/ar.html) to estimate AR, ARX (autoregressive exogenous), and ARMAX models. See [System Identification Toolbox](http://www.mathworks.com/help/ident/ug/estimating-ar-and-arma-models.html) and [Econometrics Toolbox](http://www.mathworks.com/help/econ/arima.estimate.html) for more information.
-   [Julia](https://en.wikipedia.org/wiki/Julia_(programming_language) "Julia (programming language)") has some community driven packages that implement fitting with an ARMA model such as [_arma.jl_](https://github.com/joefowler/ARMA.jl).
-   [Statsmodels](https://en.wikipedia.org/wiki/Statsmodels "Statsmodels") Python module includes many models and functions for time series analysis, including ARMA. Formerly part of [Scikit-learn](https://en.wikipedia.org/wiki/Scikit-learn "Scikit-learn") it is now stand-alone and integrates well with [Pandas](https://en.wikipedia.org/wiki/Pandas_(software) "Pandas (software)"). [See here for more details](http://statsmodels.sourceforge.net/).
-   [PyFlux](https://en.wikipedia.org/w/index.php?title=PyFlux&action=edit&redlink=1 "PyFlux (page does not exist)") has a Python-based implementation of ARIMAX models, including Bayesian ARIMAX models.
-   [IMSL Numerical Libraries](https://en.wikipedia.org/wiki/IMSL_Numerical_Libraries "IMSL Numerical Libraries") are libraries of numerical analysis functionality including ARMA and ARIMA procedures implemented in standard programming languages like C, Java, C# .NET, and Fortran.
-   [gretl](https://en.wikipedia.org/wiki/Gretl "Gretl") can also estimate ARMA model, [see here where it's mentioned](http://constantdream.wordpress.com/2008/03/16/gnu-regression-econometrics-and-time-series-library-gretl/).
-   [GNU Octave](https://en.wikipedia.org/wiki/GNU_Octave "GNU Octave") can estimate AR models using functions from the extra package [octave-forge](http://octave.sourceforge.net/).
-   [Stata](https://en.wikipedia.org/wiki/Stata "Stata") includes the function _arima_ which can estimate ARMA and [ARIMA](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average "Autoregressive integrated moving average") models. [See here for more details](https://www.stata.com/help.cgi?arima.).
-   [SuanShu](https://en.wikipedia.org/w/index.php?title=SuanShu&action=edit&redlink=1 "SuanShu (page does not exist)") is a Java library of numerical methods, including comprehensive statistics packages, in which univariate/multivariate ARMA, ARIMA, ARMAX, etc. models are implemented in an object-oriented approach. These implementations are documented in ["SuanShu, a Java numerical and statistical library"](http://www.numericalmethod.com/javadoc/suanshu/).
-   [SAS](https://en.wikipedia.org/wiki/SAS_(software) "SAS (software)") has an econometric package, ETS, that estimates ARIMA models. [See here for more details](https://web.archive.org/web/20110930032431/http://support.sas.com/rnd/app/ets/proc/ets_arima.html).

## Applications\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=11 "Edit section: Applications")\]

ARMA is appropriate when a system is a function of a series of unobserved shocks (the MA or moving average part) as well as its own behavior. For example, stock prices may be shocked by fundamental information as well as exhibiting technical trending and [mean-reversion](https://en.wikipedia.org/wiki/Mean_reversion_(finance) "Mean reversion (finance)") effects due to market participants.\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

## Generalizations\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=12 "Edit section: Generalizations")\]

The dependence of _X__t_ on past values and the error terms εt is assumed to be linear unless specified otherwise. If the dependence is nonlinear, the model is specifically called a _nonlinear moving average_ (NMA), _nonlinear autoregressive_ (NAR), or _nonlinear autoregressive–moving-average_ (NARMA) model.

Autoregressive–moving-average models can be generalized in other ways. See also [autoregressive conditional heteroskedasticity](https://en.wikipedia.org/wiki/Autoregressive_conditional_heteroskedasticity "Autoregressive conditional heteroskedasticity") (ARCH) models and [autoregressive integrated moving average](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average "Autoregressive integrated moving average") (ARIMA) models. If multiple time series are to be fitted then a vector ARIMA (or VARIMA) model may be fitted. If the time-series in question exhibits long memory then fractional ARIMA (FARIMA, sometimes called ARFIMA) modelling may be appropriate: see [Autoregressive fractionally integrated moving average](https://en.wikipedia.org/wiki/Autoregressive_fractionally_integrated_moving_average "Autoregressive fractionally integrated moving average"). If the data is thought to contain seasonal effects, it may be modeled by a SARIMA (seasonal ARIMA) or a periodic ARMA model.

Another generalization is the _multiscale autoregressive_ (MAR) model. A MAR model is indexed by the nodes of a tree, whereas a standard (discrete time) autoregressive model is indexed by integers.

Note that the ARMA model is a **univariate** model. Extensions for the multivariate case are the [vector autoregression](https://en.wikipedia.org/wiki/Vector_autoregression "Vector autoregression") (VAR) and Vector Autoregression Moving-Average (VARMA).

### Autoregressive–moving-average model with exogenous inputs model (ARMAX model)\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=13 "Edit section: Autoregressive–moving-average model with exogenous inputs model (ARMAX model)")\]

The notation ARMAX(_p_, _q_, _b_) refers to the model with _p_ autoregressive terms, _q_ moving average terms and _b_ exogenous inputs terms. This model contains the AR(_p_) and MA(_q_) models and a linear combination of the last _b_ terms of a known and external time series ![d_{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3d8ef37713c9f3f4bec0cf6f81af955876285967). It is given by:

![{\displaystyle X_{t}=\varepsilon _{t}+\sum _{i=1}^{p}\varphi _{i}X_{t-i}+\sum _{i=1}^{q}\theta _{i}\varepsilon _{t-i}+\sum _{i=1}^{b}\eta _{i}d_{t-i}.\,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbc889777df3df8cf9fe960151c842f25fec1ae0)

where ![\eta _{1},\ldots ,\eta _{b}](https://wikimedia.org/api/rest_v1/media/math/render/svg/623f631464e2beae26457f8cb499a42796d38600) are the _**parameters**_ of the exogenous input ![d_{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3d8ef37713c9f3f4bec0cf6f81af955876285967).

Some nonlinear variants of models with exogenous variables have been defined: see for example [Nonlinear autoregressive exogenous model](https://en.wikipedia.org/wiki/Nonlinear_autoregressive_exogenous_model "Nonlinear autoregressive exogenous model").

Statistical packages implement the ARMAX model through the use of "exogenous" (that is, independent,) variables. Care must be taken when interpreting the output of those packages, because the estimated parameters usually (for example, in [R](https://en.wikipedia.org/wiki/R_(programming_language) "R (programming language)")[\[8\]](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_note-R.stats.arima-8) and [gretl](https://en.wikipedia.org/wiki/Gretl "Gretl")) refer to the regression:

![X_{t}-m_{t}=\varepsilon _{t}+\sum _{i=1}^{p}\varphi _{i}(X_{t-i}-m_{t-i})+\sum _{i=1}^{q}\theta _{i}\varepsilon _{t-i}.\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/a0050fd5221ad31f1694f2df868c3cebc3bef808)

where _mt_ incorporates all exogenous (or independent) variables:

![m_{t}=c+\sum _{i=0}^{b}\eta _{i}d_{t-i}.\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/f270ad045b4ebfce43376385baff7198d4f8afd4)

## See also\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=14 "Edit section: See also")\]

-   [Autoregressive integrated moving average](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average "Autoregressive integrated moving average") (ARIMA)
-   [Exponential smoothing](https://en.wikipedia.org/wiki/Exponential_smoothing "Exponential smoothing")
-   [Linear predictive coding](https://en.wikipedia.org/wiki/Linear_predictive_coding "Linear predictive coding")
-   [Predictive analytics](https://en.wikipedia.org/wiki/Predictive_analytics "Predictive analytics")
-   [Infinite impulse response](https://en.wikipedia.org/wiki/Infinite_impulse_response "Infinite impulse response")
-   [Finite impulse response](https://en.wikipedia.org/wiki/Finite_impulse_response "Finite impulse response")

## References\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=15 "Edit section: References")\]

1.  **[^](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_ref-1 "Jump up")** [Hannan, Edward James](https://en.wikipedia.org/wiki/Edward_James_Hannan "Edward James Hannan") (1970). _Multiple time series_. Wiley series in probability and mathematical statistics. New York: John Wiley and Sons.
2.  **[^](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_ref-2 "Jump up")** Whittle, P. (1951). _Hypothesis Testing in Time Series Analysis_. Almquist and Wicksell. Whittle, P. (1963). _Prediction and Regulation_. English Universities Press. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [0-8166-1147-5](https://en.wikipedia.org/wiki/Special:BookSources/0-8166-1147-5 "Special:BookSources/0-8166-1147-5").
    
    Republished as: Whittle, P. (1983). _Prediction and Regulation by Linear Least-Square Methods_. University of Minnesota Press. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [0-8166-1148-3](https://en.wikipedia.org/wiki/Special:BookSources/0-8166-1148-3 "Special:BookSources/0-8166-1148-3").
    
3.  **[^](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_ref-3 "Jump up")** [Hannan & Deistler (1988](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#CITEREFHannanDeistler1988), p. 227): [Hannan, E. J.](https://en.wikipedia.org/wiki/Edward_James_Hannan "Edward James Hannan"); Deistler, Manfred (1988). _Statistical theory of linear systems_. Wiley series in probability and mathematical statistics. New York: John Wiley and Sons.
4.  **[^](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_ref-4 "Jump up")** Box, George; Jenkins, Gwilym M.; Reinsel, Gregory C. (1994). _Time Series Analysis: Forecasting and Control_ (Third ed.). Prentice-Hall. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [0130607746](https://en.wikipedia.org/wiki/Special:BookSources/0130607746 "Special:BookSources/0130607746").
5.  **[^](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_ref-5 "Jump up")** Missouri State University. ["Model Specification, Time Series Analysis"](http://people.missouristate.edu/songfengzheng/Teaching/MTH548/Time%20Series-ch06.pdf) (PDF).
6.  **[^](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_ref-6 "Jump up")** Brockwell, P. J.; Davis, R. A. (2009). _Time Series: Theory and Methods_ (2nd ed.). New York: Springer. p. 273. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [9781441903198](https://en.wikipedia.org/wiki/Special:BookSources/9781441903198 "Special:BookSources/9781441903198").
7.  **[^](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_ref-7 "Jump up")** [Time series features in Mathematica](http://www.wolfram.com/products/applications/timeseries/features.html) [Archived](https://web.archive.org/web/20111124032002/http://www.wolfram.com/products/applications/timeseries/features.html) November 24, 2011, at the [Wayback Machine](https://en.wikipedia.org/wiki/Wayback_Machine "Wayback Machine")
8.  **[^](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model#cite_ref-R.stats.arima_8-0 "Jump up")** [ARIMA Modelling of Time Series](http://search.r-project.org/R/library/stats/html/arima.html), R documentation

## Further reading\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive%E2%80%93moving-average_model&action=edit&section=16 "Edit section: Further reading")\]

-   Mills, Terence C. (1990). [_Time Series Techniques for Economists_](https://archive.org/details/timeseriestechni0000mill). Cambridge University Press. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [0521343399](https://en.wikipedia.org/wiki/Special:BookSources/0521343399 "Special:BookSources/0521343399").
-   Percival, Donald B.; Walden, Andrew T. (1993). _Spectral Analysis for Physical Applications_. Cambridge University Press. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [052135532X](https://en.wikipedia.org/wiki/Special:BookSources/052135532X "Special:BookSources/052135532X").
-   Francq, C.; Zakoïan, J.-M. (2005), "Recent results for linear time series models with non independent innovations", in Duchesne, P.; Remillard, B. (eds.), _Statistical Modeling and Analysis for Complex Data Problems_, Springer, pp. 241–265, [CiteSeerX](https://en.wikipedia.org/wiki/CiteSeerX_(identifier) "CiteSeerX (identifier)") [10.1.1.721.1754](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.721.1754).