# Autoregressive model
In statistics, econometrics and signal processing, an **autoregressive** (**AR**) **model** is a representation of a type of random process; as such, it is used to describe certain time-varying processes in nature, economics, etc. The autoregressive model specifies that the output variable depends linearly on its own previous values and on a stochastic term (an imperfectly predictable term); thus the model is in the form of a stochastic difference equation (or recurrence relation which should not be confused with differential equation). Together with the [moving-average (MA) model](https://en.wikipedia.org/wiki/Moving-average_model "Moving-average model"), it is a special case and key component of the more general [autoregressive–moving-average](https://en.wikipedia.org/wiki/Autoregressive%E2%80%93moving-average_model "Autoregressive–moving-average model") (ARMA) and [autoregressive integrated moving average](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average "Autoregressive integrated moving average") (ARIMA) models of time series, which have a more complicated stochastic structure; it is also a special case of the vector autoregressive model (VAR), which consists of a system of more than one interlocking stochastic difference equation in more than one evolving random variable.

Contrary to the moving-average (MA) model, the autoregressive model is not always stationary as it may contain a unit root.

## Definition\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=1 "Edit section: Definition")\]

The notation ![AR(p)](https://wikimedia.org/api/rest_v1/media/math/render/svg/656b65718fc07fb84c0d8186c6e43ce76723427b) indicates an autoregressive model of order _p_. The AR(_p_) model is defined as

![X_{t}=c+\sum _{{i=1}}^{p}\varphi _{i}X_{{t-i}}+\varepsilon _{t}\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/783f17f3ab83135ed3828b73b0957735a1b63229)

where ![\varphi _{1},\ldots ,\varphi _{p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d4fdc81c8ea00ebabdeee779385a8e22e3c2b385) are the _parameters_ of the model, ![c](https://wikimedia.org/api/rest_v1/media/math/render/svg/86a67b81c2de995bd608d5b2df50cd8cd7d92455) is a constant, and ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a) is [white noise](https://en.wikipedia.org/wiki/White_noise "White noise"). This can be equivalently written using the [backshift operator](https://en.wikipedia.org/wiki/Backshift_operator "Backshift operator") _B_ as

![X_{t}=c+\sum _{{i=1}}^{p}\varphi _{i}B^{i}X_{t}+\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0b1e286924bc466350e62689efd74664287e2c3f)

so that, moving the summation term to the left side and using [polynomial notation](https://en.wikipedia.org/wiki/Polynomial_notation "Polynomial notation"), we have

![{\displaystyle \phi [B]X_{t}=c+\varepsilon _{t}\,.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b384dd193d1b8b0063a997d5a8d65434a7908880)

An autoregressive model can thus be viewed as the output of an all-[pole](https://en.wikipedia.org/wiki/Pole_(complex_analysis) "Pole (complex analysis)") [infinite impulse response](https://en.wikipedia.org/wiki/Infinite_impulse_response "Infinite impulse response") filter whose input is white noise.

Some parameter constraints are necessary for the model to remain [wide-sense stationary](https://en.wikipedia.org/wiki/Wide-sense_stationary "Wide-sense stationary"). For example, processes in the AR(1) model with ![|\varphi _{1}|\geq 1](https://wikimedia.org/api/rest_v1/media/math/render/svg/5feb9de2fe8907d308f9eaaab3ff940d54b8fbf9) are not stationary. More generally, for an AR(_p_) model to be wide-sense stationary, the roots of the polynomial ![{\displaystyle \Phi (z):=\textstyle 1-\sum _{i=1}^{p}\varphi _{i}z^{p-i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/58a0ad11bbb66b5a2819b4428f3d7e3ac9acedf8) must lie outside the [unit circle](https://en.wikipedia.org/wiki/Unit_circle "Unit circle"), i.e., each (complex) root ![z_{i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5c6e920bac39ad09fff4efef16254595091a1025) must satisfy ![{\displaystyle |z_{i}|>1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ff75c25f97e572744f6a3c93410506ce35cd1d1e) (see pages 88,90 [\[1\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-1)).

## Intertemporal effect of shocks\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=2 "Edit section: Intertemporal effect of shocks")\]

In an AR process, a one-time shock affects values of the evolving variable infinitely far into the future. For example, consider the AR(1) model ![X_{t}=c+\varphi _{1}X_{{t-1}}+\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f6cbe5ebba494a88afb245253329691a3bd101bb). A non-zero value for ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a) at say time _t_\=1 affects ![X_{1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f70b2694445a5901b24338a2e7a7e58f02a72a32) by the amount ![\varepsilon _{1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e900f9bee793f99d10877ef108da074cbca60ce). Then by the AR equation for ![X_{2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2ad47c14b8a092f182512e76c96638aea6e3bea1) in terms of ![X_{1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f70b2694445a5901b24338a2e7a7e58f02a72a32), this affects ![X_{2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2ad47c14b8a092f182512e76c96638aea6e3bea1) by the amount ![\varphi _{1}\varepsilon _{1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e6771fe396d6eec7394996b530cb986db71feea4). Then by the AR equation for ![X_3](https://wikimedia.org/api/rest_v1/media/math/render/svg/14f17eb6a51e16ea92736c904a92d8a78e73a598) in terms of ![X_{2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2ad47c14b8a092f182512e76c96638aea6e3bea1), this affects ![X_3](https://wikimedia.org/api/rest_v1/media/math/render/svg/14f17eb6a51e16ea92736c904a92d8a78e73a598) by the amount ![\varphi _{1}^{2}\varepsilon _{1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e47bea8b4509e8572bfbd52a6989c11ab084d724). Continuing this process shows that the effect of ![\varepsilon _{1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e900f9bee793f99d10877ef108da074cbca60ce) never ends, although if the process is [stationary](https://en.wikipedia.org/wiki/Stationary_process "Stationary process") then the effect diminishes toward zero in the limit.

Because each shock affects _X_ values infinitely far into the future from when they occur, any given value _X__t_ is affected by shocks occurring infinitely far into the past. This can also be seen by rewriting the autoregression

![\phi (B)X_{t}=\varepsilon _{t}\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/8c07c3c7172406b06bb1b30313744788a4b99481)

(where the constant term has been suppressed by assuming that the variable has been measured as deviations from its mean) as

![X_{t}={\frac  {1}{\phi (B)}}\varepsilon _{t}\,.](https://wikimedia.org/api/rest_v1/media/math/render/svg/788086c2d58f2233bb3ae2d8e5f7eccc17628173)

When the [polynomial division](https://en.wikipedia.org/wiki/Polynomial_long_division "Polynomial long division") on the right side is carried out, the polynomial in the backshift operator applied to ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a) has an infinite order—that is, an infinite number of lagged values of ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a) appear on the right side of the equation.

## Characteristic polynomial\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=3 "Edit section: Characteristic polynomial")\]

The [autocorrelation function](https://en.wikipedia.org/wiki/Autocorrelation_function "Autocorrelation function") of an AR(_p_) process can be expressed as\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

![\rho (\tau )=\sum _{{k=1}}^{p}a_{k}y_{k}^{{-|\tau |}},](https://wikimedia.org/api/rest_v1/media/math/render/svg/979241068653d54f8ce728e1d16e45df688a69fc)

where ![y_{k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b2ab0248723a410cc2c67ce06ad5c043dcbb933) are the roots of the polynomial

![\phi (B)=1-\sum _{{k=1}}^{p}\varphi _{k}B^{k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dfea5de760da3cb674b9aa8ea3509d86ab7e3bd5)

where _B_ is the [backshift operator](https://en.wikipedia.org/wiki/Backshift_operator "Backshift operator"), where ![\phi (\cdot )](https://wikimedia.org/api/rest_v1/media/math/render/svg/7ead8078ac455302b763cfc6a02b75282077140b) is the function defining the autoregression, and where ![\varphi _{k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dad86b92f0c76d343e12c4a90b368834329bd5d6) are the coefficients in the autoregression.

The autocorrelation function of an AR(_p_) process is a sum of decaying exponentials.

-   Each real root contributes a component to the autocorrelation function that decays exponentially.
-   Similarly, each pair of complex conjugate roots contributes an exponentially damped oscillation.

## Graphs of AR(_p_) processes\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=4 "Edit section: Graphs of AR(p) processes")\]

[!["Figure has 5 plots of AR processes. AR(0) and AR(0.3) are white noise or look like white noise. AR(0.9) has some large scale oscillating structure."](https://upload.wikimedia.org/wikipedia/commons/thumb/c/ce/ArTimeSeries.svg/220px-ArTimeSeries.svg.png)](https://en.wikipedia.org/wiki/File:ArTimeSeries.svg)

AR(0); AR(1) with AR parameter 0.3; AR(1) with AR parameter 0.9; AR(2) with AR parameters 0.3 and 0.3; and AR(2) with AR parameters 0.9 and −0.8

The simplest AR process is AR(0), which has no dependence between the terms. Only the error/innovation/noise term contributes to the output of the process, so in the figure, AR(0) corresponds to white noise.

For an AR(1) process with a positive ![\varphi ](https://wikimedia.org/api/rest_v1/media/math/render/svg/33ee699558d09cf9d653f6351f9fda0b2f4aaa3e), only the previous term in the process and the noise term contribute to the output. If ![\varphi ](https://wikimedia.org/api/rest_v1/media/math/render/svg/33ee699558d09cf9d653f6351f9fda0b2f4aaa3e) is close to 0, then the process still looks like white noise, but as ![\varphi ](https://wikimedia.org/api/rest_v1/media/math/render/svg/33ee699558d09cf9d653f6351f9fda0b2f4aaa3e) approaches 1, the output gets a larger contribution from the previous term relative to the noise. This results in a "smoothing" or integration of the output, similar to a low pass filter.

For an AR(2) process, the previous two terms and the noise term contribute to the output. If both ![\varphi _{1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d7daf493c8f6ef669c04c7b9715532fc35d12d60) and ![\varphi _{2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c08631714273b6c8edaa9573ef3d8c548314a930) are positive, the output will resemble a low pass filter, with the high frequency part of the noise decreased. If ![\varphi _{1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d7daf493c8f6ef669c04c7b9715532fc35d12d60) is positive while ![\varphi _{2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c08631714273b6c8edaa9573ef3d8c548314a930) is negative, then the process favors changes in sign between terms of the process. The output oscillates. This can be likened to edge detection or detection of change in direction.

## Example: An AR(1) process\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=5 "Edit section: Example: An AR(1) process")\]

An AR(1) process is given by:

![X_{t}=c+\varphi X_{{t-1}}+\varepsilon _{t}\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/d5f44a8ddc9b27d332341c319ee16e6c498834e6)

where ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a) is a white noise process with zero mean and constant variance ![\sigma _{\varepsilon }^{2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eec379b86e73255492d3266c76f6e17acfdfabd1). (Note: The subscript on ![\varphi _{1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d7daf493c8f6ef669c04c7b9715532fc35d12d60) has been dropped.) The process is [wide-sense stationary](https://en.wikipedia.org/wiki/Wide-sense_stationary "Wide-sense stationary") if ![|\varphi |<1](https://wikimedia.org/api/rest_v1/media/math/render/svg/7ac88cf3e11f7577b756abedbee667cce5069563) since it is obtained as the output of a stable filter whose input is white noise. (If ![\varphi =1](https://wikimedia.org/api/rest_v1/media/math/render/svg/a4d2b07a5e6f6058e04da966ccdc8506fe8ffeb2) then the variance of ![X_{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/82120d04dfb3cbadc4912951dd12b5568c9cd8f3) depends on time lag t, so that the variance of the series diverges to infinity as t goes to infinity, and is therefore not wide sense stationary.) Assuming ![|\varphi |<1](https://wikimedia.org/api/rest_v1/media/math/render/svg/7ac88cf3e11f7577b756abedbee667cce5069563), the mean ![\operatorname {E}(X_{t})](https://wikimedia.org/api/rest_v1/media/math/render/svg/be42d3e2b3cfe283a64cf222c06972633e8ded66) is identical for all values of _t_ by the very definition of wide sense stationarity. If the mean is denoted by ![\mu ](https://wikimedia.org/api/rest_v1/media/math/render/svg/9fd47b2a39f7a7856952afec1f1db72c67af6161), it follows from

![\operatorname {E}(X_{t})=\operatorname {E}(c)+\varphi \operatorname {E}(X_{{t-1}})+\operatorname {E}(\varepsilon _{t}),](https://wikimedia.org/api/rest_v1/media/math/render/svg/65fa8cda0ab1dc44df325cbcd2a855308a58c265)

that

![\mu =c+\varphi \mu +0,](https://wikimedia.org/api/rest_v1/media/math/render/svg/a3a82236d6a79b0e4a90c9be4719b2b7b42a16e7)

and hence

![\mu ={\frac  {c}{1-\varphi }}.](https://wikimedia.org/api/rest_v1/media/math/render/svg/2a543bb44f44e1019164134609dfdfce2ec5f0c0)

In particular, if ![c=0](https://wikimedia.org/api/rest_v1/media/math/render/svg/d9ee918699d0cb4b8c633cc1f520a8a7a174f44a), then the mean is 0.

The [variance](https://en.wikipedia.org/wiki/Variance "Variance") is

![{\textrm  {var}}(X_{t})=\operatorname {E}(X_{t}^{2})-\mu ^{2}={\frac  {\sigma _{\varepsilon }^{2}}{1-\varphi ^{2}}},](https://wikimedia.org/api/rest_v1/media/math/render/svg/4f1742b6092c63b09414e86c9e208b2da49c8dcf)

where ![\sigma _{\varepsilon }](https://wikimedia.org/api/rest_v1/media/math/render/svg/04852f481494a445c9f5b9082df1ead002c098a2) is the standard deviation of ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a). This can be shown by noting that

![{\textrm  {var}}(X_{t})=\varphi ^{2}{\textrm  {var}}(X_{{t-1}})+\sigma _{\varepsilon }^{2},](https://wikimedia.org/api/rest_v1/media/math/render/svg/c5594a5bf1cd9c13fb15eb23763328c684b41778)

and then by noticing that the quantity above is a stable fixed point of this relation.

The [autocovariance](https://en.wikipedia.org/wiki/Autocovariance "Autocovariance") is given by

![B_{n}=\operatorname {E}(X_{{t+n}}X_{t})-\mu ^{2}={\frac  {\sigma _{\varepsilon }^{2}}{1-\varphi ^{2}}}\,\,\varphi ^{{|n|}}.](https://wikimedia.org/api/rest_v1/media/math/render/svg/8437c88291c59fdbb8055f7630becfb993b1fb17)

It can be seen that the autocovariance function decays with a decay time (also called [time constant](https://en.wikipedia.org/wiki/Time_constant "Time constant")) of ![\tau =-1/\ln(\varphi )](https://wikimedia.org/api/rest_v1/media/math/render/svg/3123a373899991db470b9ca3d1c6dfbdc52e8ee1) \[to see this, write ![{\displaystyle B_{n}=K\varphi ^{|n|}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/96f03651a2a39afbf91e418f3d5fcb631c177cb2) where ![K](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b76fce82a62ed5461908f0dc8f037de4e3686b0) is independent of ![n](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b). Then note that ![{\displaystyle \varphi ^{|n|}=e^{|n|\ln \varphi }}](https://wikimedia.org/api/rest_v1/media/math/render/svg/883437b5e9bf20971cfa318f6e9277242d642481) and match this to the exponential decay law ![e^{{-n/\tau }}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3597f2f81cf3ea9e89d7bd861d0121ee343d545e)\].

The [spectral density](https://en.wikipedia.org/wiki/Spectral_density "Spectral density") function is the [Fourier transform](https://en.wikipedia.org/wiki/Fourier_transform "Fourier transform") of the autocovariance function. In discrete terms this will be the discrete-time Fourier transform:

![\Phi (\omega )={\frac  {1}{{\sqrt  {2\pi }}}}\,\sum _{{n=-\infty }}^{\infty }B_{n}e^{{-i\omega n}}={\frac  {1}{{\sqrt  {2\pi }}}}\,\left({\frac  {\sigma _{\varepsilon }^{2}}{1+\varphi ^{2}-2\varphi \cos(\omega )}}\right).](https://wikimedia.org/api/rest_v1/media/math/render/svg/7fd707a70fc78fabba4b103d6099d2a75f109d02)

This expression is periodic due to the discrete nature of the ![X_{j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ca3cb1ef7c9f25e85e1957e4eb58a72fa16a0066), which is manifested as the cosine term in the denominator. If we assume that the sampling time (![\Delta t=1](https://wikimedia.org/api/rest_v1/media/math/render/svg/26978f1c5f3ac3161ce7635cbde2a207c7519aab)) is much smaller than the decay time (![\tau ](https://wikimedia.org/api/rest_v1/media/math/render/svg/38a7dcde9730ef0853809fefc18d88771f95206c)), then we can use a continuum approximation to ![B_{n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f568bf6d34e97b9fdda0dc7e276d6c4501d2045):

![B(t)\approx {\frac  {\sigma _{\varepsilon }^{2}}{1-\varphi ^{2}}}\,\,\varphi ^{{|t|}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/23ab1061089249aaff9c9522ab7ba1da4296f38b)

which yields a [Lorentzian profile](https://en.wikipedia.org/wiki/Cauchy_distribution "Cauchy distribution") for the spectral density:

![\Phi (\omega )={\frac  {1}{{\sqrt  {2\pi }}}}\,{\frac  {\sigma _{\varepsilon }^{2}}{1-\varphi ^{2}}}\,{\frac  {\gamma }{\pi (\gamma ^{2}+\omega ^{2})}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/09c4d8d2e045f649f287fc359418e5e65e69f042)

where ![\gamma =1/\tau ](https://wikimedia.org/api/rest_v1/media/math/render/svg/64537ae1c00fe728d4fc64b69a72daec33b8e99c) is the angular frequency associated with the decay time ![\tau ](https://wikimedia.org/api/rest_v1/media/math/render/svg/38a7dcde9730ef0853809fefc18d88771f95206c).

An alternative expression for ![X_{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/82120d04dfb3cbadc4912951dd12b5568c9cd8f3) can be derived by first substituting ![c+\varphi X_{{t-2}}+\varepsilon _{{t-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7787d0d39eb7a51cbebaf48cb00e775bd56bf28a) for ![X_{{t-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7cdeab0b9b98bc0b52250537bc0234d7d3de6b60) in the defining equation. Continuing this process _N_ times yields

![X_{t}=c\sum _{{k=0}}^{{N-1}}\varphi ^{k}+\varphi ^{N}X_{{t-N}}+\sum _{{k=0}}^{{N-1}}\varphi ^{k}\varepsilon _{{t-k}}.](https://wikimedia.org/api/rest_v1/media/math/render/svg/eb2bc722c92ed8456fb6afbc49249c5235904475)

For _N_ approaching infinity, ![\varphi ^{N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a3c7d06db11de79871f23fce1a87a85a61e19f12) will approach zero and:

![X_{t}={\frac  {c}{1-\varphi }}+\sum _{{k=0}}^{\infty }\varphi ^{k}\varepsilon _{{t-k}}.](https://wikimedia.org/api/rest_v1/media/math/render/svg/71dc254dbf8d8b18ea6b62249f047a0982a9d4c0)

It is seen that ![X_{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/82120d04dfb3cbadc4912951dd12b5568c9cd8f3) is white noise convolved with the ![\varphi ^{k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/718a443a1669e482cf76903e77f49dc3f9a286d7) kernel plus the constant mean. If the white noise ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a) is a [Gaussian process](https://en.wikipedia.org/wiki/Gaussian_process "Gaussian process") then ![X_{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/82120d04dfb3cbadc4912951dd12b5568c9cd8f3) is also a Gaussian process. In other cases, the [central limit theorem](https://en.wikipedia.org/wiki/Central_limit_theorem "Central limit theorem") indicates that ![X_{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/82120d04dfb3cbadc4912951dd12b5568c9cd8f3) will be approximately normally distributed when ![\varphi ](https://wikimedia.org/api/rest_v1/media/math/render/svg/33ee699558d09cf9d653f6351f9fda0b2f4aaa3e) is close to one.

### Explicit mean/difference form of AR(1) process\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=6 "Edit section: Explicit mean/difference form of AR(1) process")\]

The AR(1) model is the discrete time analogy of the continuous [Ornstein-Uhlenbeck process](https://en.wikipedia.org/wiki/Ornstein-Uhlenbeck_process "Ornstein-Uhlenbeck process"). It is therefore sometimes useful to understand the properties of the AR(1) model cast in an equivalent form. In this form, the AR(1) model, with process parameter ![\theta ](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e5ab2664b422d53eb0c7df3b87e1360d75ad9af) is given by:

![{\displaystyle X_{t+1}=X_{t}+(1-\theta )(\mu -X_{t})+\epsilon _{t+1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c24010e8ff3c011272635f2dfeb5373db65e1999), where ![|\theta |<1\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/5780668779972c655ed2ab5186f7e3074ea4530d) and ![\mu ](https://wikimedia.org/api/rest_v1/media/math/render/svg/9fd47b2a39f7a7856952afec1f1db72c67af6161) is the model mean.

By putting this in the form ![{\displaystyle X_{t+1}=c+\phi X_{t}\ +\epsilon _{t+1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4e1fe129b79c8ea70d4aaf2a822568dc570c6b35), and then expanding the series for ![{\displaystyle X_{t+n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ecaadfc780688ec940f11eba049ce1b6808bf4ae), one can show that:

![{\displaystyle \operatorname {E} (X_{t+n}|X_{t})=\mu \left[1-\theta ^{n}\right]+X_{t}\theta ^{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/57e7ce545d36dfb0de17a55881ba8322e99955a5), and

![{\displaystyle \operatorname {Var} (X_{t+n}|X_{t})=\sigma ^{2}{\frac {1-\theta ^{2n}}{1-\theta ^{2}}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/faae1ccdfe1d391ae209a92012a05e69afe032ff).

## Choosing the maximum lag\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=7 "Edit section: Choosing the maximum lag")\]

The partial autocorrelation of an AR(p) process equals zero at lag which is not bigger than order of p\[_[clarification needed](https://en.wikipedia.org/wiki/Wikipedia:Please_clarify "Wikipedia:Please clarify")_\] and provides a good model for the correlation between ![X_{1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f70b2694445a5901b24338a2e7a7e58f02a72a32)and ![{\displaystyle X_{p+1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b23c641f44ec9de03394a88353f0393cea841cc0), so the appropriate maximum lag is the one beyond which the partial autocorrelations are all zero.

## Calculation of the AR parameters\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=8 "Edit section: Calculation of the AR parameters")\]

There are many ways to estimate the coefficients, such as the [ordinary least squares](https://en.wikipedia.org/wiki/Ordinary_least_squares "Ordinary least squares") procedure or [method of moments](https://en.wikipedia.org/wiki/Method_of_moments_(statistics) "Method of moments (statistics)") (through Yule–Walker equations).

The AR(_p_) model is given by the equation

![X_{t}=\sum _{{i=1}}^{p}\varphi _{i}X_{{t-i}}+\varepsilon _{t}.\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/b1a017e273d484ea82c3c0effe3153b1e991a0ef)

It is based on parameters ![\varphi _{i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/70503774fb21be77396899900d3aa1e47d8f9e10) where _i_ = 1, ..., _p_. There is a direct correspondence between these parameters and the covariance function of the process, and this correspondence can be inverted to determine the parameters from the autocorrelation function (which is itself obtained from the covariances). This is done using the Yule–Walker equations.

### Yule–Walker equations\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=9 "Edit section: Yule–Walker equations")\]

The Yule–Walker equations, named for [Udny Yule](https://en.wikipedia.org/wiki/Udny_Yule "Udny Yule") and [Gilbert Walker](https://en.wikipedia.org/wiki/Gilbert_Walker_(physicist) "Gilbert Walker (physicist)"),[\[2\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-2)[\[3\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-3) are the following set of equations.[\[4\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-4)

![{\displaystyle \gamma _{m}=\sum _{k=1}^{p}\varphi _{k}\gamma _{m-k}+\sigma _{\varepsilon }^{2}\delta _{m,0},}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9da60172903d9e7119978e11c9b113da40544a75)

where _m_ = 0, …, _p_, yielding _p_ + 1 equations. Here ![\gamma _{m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/27a890b6f03d91a6f3f1033e4ffdf6b2c46c7737) is the autocovariance function of Xt, ![\sigma _{\varepsilon }](https://wikimedia.org/api/rest_v1/media/math/render/svg/04852f481494a445c9f5b9082df1ead002c098a2) is the standard deviation of the input noise process, and ![\delta _{{m,0}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e1370316eefa8164f8231f804f30d9e9a15cc652) is the [Kronecker delta function](https://en.wikipedia.org/wiki/Kronecker_delta_function "Kronecker delta function").

Because the last part of an individual equation is non-zero only if _m_ = 0, the set of equations can be solved by representing the equations for _m_ > 0 in matrix form, thus getting the equation

![{\displaystyle {\begin{bmatrix}\gamma _{1}\\\gamma _{2}\\\gamma _{3}\\\vdots \\\gamma _{p}\\\end{bmatrix}}={\begin{bmatrix}\gamma _{0}&\gamma _{-1}&\gamma _{-2}&\cdots \\\gamma _{1}&\gamma _{0}&\gamma _{-1}&\cdots \\\gamma _{2}&\gamma _{1}&\gamma _{0}&\cdots \\\vdots &\vdots &\vdots &\ddots \\\gamma _{p-1}&\gamma _{p-2}&\gamma _{p-3}&\cdots \\\end{bmatrix}}{\begin{bmatrix}\varphi _{1}\\\varphi _{2}\\\varphi _{3}\\\vdots \\\varphi _{p}\\\end{bmatrix}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3a564a8ed89ab0e811cec86e6381723792950663)

which can be solved for all ![{\displaystyle \{\varphi _{m};m=1,2,\dots ,p\}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a852eb40a2580da26a00424bfa85c14c077bc73e) The remaining equation for _m_ = 0 is

![{\displaystyle \gamma _{0}=\sum _{k=1}^{p}\varphi _{k}\gamma _{-k}+\sigma _{\varepsilon }^{2},}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9b026ab9a1802d7f6365a76f22b966a46f39f3f4)

which, once ![{\displaystyle \{\varphi _{m};m=1,2,\dots ,p\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/11b162c79b064fc3de8d868c0a5210897b051f0f) are known, can be solved for ![\sigma _{\varepsilon }^{2}.](https://wikimedia.org/api/rest_v1/media/math/render/svg/aa5d61c2a70c33444023a77f42f7502a2abd7c18)

An alternative formulation is in terms of the [autocorrelation function](https://en.wikipedia.org/wiki/Autocorrelation_function "Autocorrelation function"). The AR parameters are determined by the first _p_+1 elements ![\rho (\tau )](https://wikimedia.org/api/rest_v1/media/math/render/svg/7f1b4786ec22c80e8b5d81429869524e2fadca5e) of the autocorrelation function. The full autocorrelation function can then be derived by recursively calculating [\[5\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-Storch-5)

![\rho (\tau )=\sum _{{k=1}}^{p}\varphi _{k}\rho (k-\tau )](https://wikimedia.org/api/rest_v1/media/math/render/svg/b7510506c4854869e268ae4a004ffdeaf07a0713)

Examples for some Low-order AR(_p_) processes

-   _p_\=1
-   _p_\=2

### Estimation of AR parameters\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=10 "Edit section: Estimation of AR parameters")\]

The above equations (the Yule–Walker equations) provide several routes to estimating the parameters of an AR(_p_) model, by replacing the theoretical covariances with estimated values.[\[6\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-6) Some of these variants can be described as follows:

-   Estimation of autocovariances or autocorrelations. Here each of these terms is estimated separately, using conventional estimates. There are different ways of doing this and the choice between these affects the properties of the estimation scheme. For example, negative estimates of the variance can be produced by some choices.
-   Formulation as a [least squares regression](https://en.wikipedia.org/wiki/Least_squares_regression "Least squares regression") problem in which an ordinary least squares prediction problem is constructed, basing prediction of values of _X__t_ on the _p_ previous values of the same series. This can be thought of as a forward-prediction scheme. The [normal equations](https://en.wikipedia.org/wiki/Normal_equations "Normal equations") for this problem can be seen to correspond to an approximation of the matrix form of the Yule–Walker equations in which each appearance of an autocovariance of the same lag is replaced by a slightly different estimate.
-   Formulation as an extended form of ordinary least squares prediction problem. Here two sets of prediction equations are combined into a single estimation scheme and a single set of normal equations. One set is the set of forward-prediction equations and the other is a corresponding set of backward prediction equations, relating to the backward representation of the AR model:

![X_{t}=c+\sum _{{i=1}}^{p}\varphi _{i}X_{{t-i}}+\varepsilon _{t}^{*}\,.](https://wikimedia.org/api/rest_v1/media/math/render/svg/864bb5b2b097012272d52180553e16d4139d2d90)

Here predicted values of _X__t_ would be based on the _p_ future values of the same series.\[_[clarification needed](https://en.wikipedia.org/wiki/Wikipedia:Please_clarify "Wikipedia:Please clarify")_\] This way of estimating the AR parameters is due to Burg,[\[7\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-Burg-7) and is called the Burg method:[\[8\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-Brockwell-8) Burg and later authors called these particular estimates "maximum entropy estimates",[\[9\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-Burg1-9) but the reasoning behind this applies to the use of any set of estimated AR parameters. Compared to the estimation scheme using only the forward prediction equations, different estimates of the autocovariances are produced, and the estimates have different stability properties. Burg estimates are particularly associated with [maximum entropy spectral estimation](https://en.wikipedia.org/wiki/Maximum_entropy_spectral_estimation "Maximum entropy spectral estimation").[\[10\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-Bos-10)

Other possible approaches to estimation include [maximum likelihood estimation](https://en.wikipedia.org/wiki/Maximum_likelihood_estimation "Maximum likelihood estimation"). Two distinct variants of maximum likelihood are available: in one (broadly equivalent to the forward prediction least squares scheme) the likelihood function considered is that corresponding to the conditional distribution of later values in the series given the initial _p_ values in the series; in the second, the likelihood function considered is that corresponding to the unconditional joint distribution of all the values in the observed series. Substantial differences in the results of these approaches can occur if the observed series is short, or if the process is close to non-stationarity.

## Spectrum\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=11 "Edit section: Spectrum")\]

[![AutocorrTimeAr.svg](https://upload.wikimedia.org/wikipedia/commons/thumb/6/65/AutocorrTimeAr.svg/220px-AutocorrTimeAr.svg.png)](https://en.wikipedia.org/wiki/File:AutocorrTimeAr.svg)

[![AutoCorrAR.svg](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8b/AutoCorrAR.svg/220px-AutoCorrAR.svg.png)](https://en.wikipedia.org/wiki/File:AutoCorrAR.svg)

The [power spectral density](https://en.wikipedia.org/wiki/Spectral_density#Power_spectral_density "Spectral density") (PSD) of an AR(_p_) process with noise variance ![{\mathrm  {Var}}(Z_{t})=\sigma _{Z}^{2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fcf6634824713d3cfd153951776fe39e92578b21) is[\[5\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-Storch-5)

![{\displaystyle S(f)={\frac {\sigma _{Z}^{2}}{|1-\sum _{k=1}^{p}\varphi _{k}e^{-i2\pi fk}|^{2}}}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/42f50b7ac757b2de256f1e9ff1571e969884c257)

### AR(0)\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=12 "Edit section: AR(0)")\]

For white noise (AR(0))

![S(f)=\sigma _{Z}^{2}.](https://wikimedia.org/api/rest_v1/media/math/render/svg/06468b780d3e82778416cc74ff45f2bb6298547f)

### AR(1)\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=13 "Edit section: AR(1)")\]

For AR(1)

![S(f)={\frac  {\sigma _{Z}^{2}}{|1-\varphi _{1}e^{{-2\pi if}}|^{2}}}={\frac  {\sigma _{Z}^{2}}{1+\varphi _{1}^{2}-2\varphi _{1}\cos 2\pi f}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fe899e2c744e152309b413956cb163d64218246b)

### AR(2)\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=14 "Edit section: AR(2)")\]

AR(2) processes can be split into three groups depending on the characteristics of their roots:

![z_{1},z_{2}={\frac  {1}{2}}\left(\varphi _{1}\pm {\sqrt  {\varphi _{1}^{2}+4\varphi _{2}}}\right)](https://wikimedia.org/api/rest_v1/media/math/render/svg/c045babe182e8829fee88125f44fa6c2a67400d1)

-   When ![\varphi _{1}^{2}+4\varphi _{2}<0](https://wikimedia.org/api/rest_v1/media/math/render/svg/0458ca96d21393755f25e547fb527f92a5b25272), the process has a pair of complex-conjugate roots, creating a mid-frequency peak at:

![f^{*}={\frac  {1}{2\pi }}\cos ^{{-1}}\left({\frac  {\varphi _{1}(\varphi _{2}-1)}{4\varphi _{2}}}\right)](https://wikimedia.org/api/rest_v1/media/math/render/svg/bd66c7c06b8077ddc035d695d90c41d883878779)

Otherwise the process has real roots, and:

The process is non-stationary when the roots are outside the unit circle. The process is stable when the roots are within the unit circle, or equivalently when the coefficients are in the triangle ![-1\leq \varphi _{2}\leq 1-|\varphi _{1}|](https://wikimedia.org/api/rest_v1/media/math/render/svg/174a4fea8bdb965bfce378f7c22e1333141e85ea).

The full PSD function can be expressed in real form as:

![S(f)={\frac  {\sigma _{Z}^{2}}{1+\varphi _{1}^{2}+\varphi _{2}^{2}-2\varphi _{1}(1-\varphi _{2})\cos(2\pi f)-2\varphi _{2}\cos(4\pi f)}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a013a00f38c6fa6be16d25f4b30ed3842b88a04e)

## Implementations in statistics packages\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=15 "Edit section: Implementations in statistics packages")\]

-   [R](https://en.wikipedia.org/wiki/R_(programming_language) "R (programming language)"), the _stats_ package includes an _ar_ function.[\[11\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-11)
-   [MATLAB](https://en.wikipedia.org/wiki/Matlab_(programming_language) "Matlab (programming language)")'s Econometrics Toolbox[\[12\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-12) and System Identification Toolbox[\[13\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-13) includes autoregressive models[\[14\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-14)
-   [Matlab](https://en.wikipedia.org/wiki/Matlab_(programming_language) "Matlab (programming language)") and [Octave](https://en.wikipedia.org/wiki/Octave_(programming_language) "Octave (programming language)"): the _TSA toolbox_ contains several estimation functions for uni-variate, [multivariate](https://en.wikipedia.org/wiki/Multivariate_statistics "Multivariate statistics") and adaptive autoregressive models.[\[15\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-15)
-   [PyMC3](https://en.wikipedia.org/wiki/PyMC3 "PyMC3"): the Bayesian statistics and probabilistic programming framework supports autoregressive modes with _p_ lags.
-   _bayesloop_ supports parameter inference and model selection for the AR-1 process with time-varying parameters.[\[16\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-16)
-   [Python](https://en.wikipedia.org/wiki/Python_(programming_language) "Python (programming language)"): implementation in statsmodels.[\[17\]](https://en.wikipedia.org/wiki/Autoregressive_model#cite_note-17)

## Impulse response\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=16 "Edit section: Impulse response")\]

The [impulse response](https://en.wikipedia.org/wiki/Impulse_response "Impulse response") of a system is the change in an evolving variable in response to a change in the value of a shock term _k_ periods earlier, as a function of _k_. Since the AR model is a special case of the vector autoregressive model, the computation of the impulse response in [vector autoregression#impulse response](https://en.wikipedia.org/wiki/Vector_autoregression#Impulse_response "Vector autoregression") applies here.

## _n_\-step-ahead forecasting\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=17 "Edit section: n-step-ahead forecasting")\]

Once the parameters of the autoregression

![X_{t}=c+\sum _{{i=1}}^{p}\varphi _{i}X_{{t-i}}+\varepsilon _{t}\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/783f17f3ab83135ed3828b73b0957735a1b63229)

have been estimated, the autoregression can be used to forecast an arbitrary number of periods into the future. First use _t_ to refer to the first period for which data is not yet available; substitute the known preceding values _X__t-i_ for _i=_1, ..., _p_ into the autoregressive equation while setting the error term ![\varepsilon _{t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c1ff8b8945e6a4fccf6071f806b9ef232492b9a) equal to zero (because we forecast _X__t_ to equal its expected value, and the expected value of the unobserved error term is zero). The output of the autoregressive equation is the forecast for the first unobserved period. Next, use _t_ to refer to the _next_ period for which data is not yet available; again the autoregressive equation is used to make the forecast, with one difference: the value of _X_ one period prior to the one now being forecast is not known, so its expected value—the predicted value arising from the previous forecasting step—is used instead. Then for future periods the same procedure is used, each time using one more forecast value on the right side of the predictive equation until, after _p_ predictions, all _p_ right-side values are predicted values from preceding steps.

There are four sources of uncertainty regarding predictions obtained in this manner: (1) uncertainty as to whether the autoregressive model is the correct model; (2) uncertainty about the accuracy of the forecasted values that are used as lagged values in the right side of the autoregressive equation; (3) uncertainty about the true values of the autoregressive coefficients; and (4) uncertainty about the value of the error term ![\varepsilon _{t}\,](https://wikimedia.org/api/rest_v1/media/math/render/svg/0dddd630dd121297ad959b33a2adf8d58c3101ea) for the period being predicted. Each of the last three can be quantified and combined to give a [confidence interval](https://en.wikipedia.org/wiki/Confidence_interval "Confidence interval") for the _n_\-step-ahead predictions; the confidence interval will become wider as _n_ increases because of the use of an increasing number of estimated values for the right-side variables.

## Evaluating the quality of forecasts\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=18 "Edit section: Evaluating the quality of forecasts")\]

The predictive performance of the autoregressive model can be assessed as soon as estimation has been done if [cross-validation](https://en.wikipedia.org/wiki/Cross-validation_(statistics) "Cross-validation (statistics)") is used. In this approach, some of the initially available data was used for parameter estimation purposes, and some (from available observations later in the data set) was held back for out-of-sample testing. Alternatively, after some time has passed after the parameter estimation was conducted, more data will have become available and predictive performance can be evaluated then using the new data.

In either case, there are two aspects of predictive performance that can be evaluated: one-step-ahead and _n_\-step-ahead performance. For one-step-ahead performance, the estimated parameters are used in the autoregressive equation along with observed values of _X_ for all periods prior to the one being predicted, and the output of the equation is the one-step-ahead forecast; this procedure is used to obtain forecasts for each of the out-of-sample observations. To evaluate the quality of _n_\-step-ahead forecasts, the forecasting procedure in the previous section is employed to obtain the predictions.

Given a set of predicted values and a corresponding set of actual values for _X_ for various time periods, a common evaluation technique is to use the [mean squared prediction error](https://en.wikipedia.org/wiki/Mean_squared_prediction_error "Mean squared prediction error"); other measures are also available (see [forecasting#forecasting accuracy](https://en.wikipedia.org/wiki/Forecasting#Forecasting_accuracy "Forecasting")).

The question of how to interpret the measured forecasting accuracy arises—for example, what is a "high" (bad) or a "low" (good) value for the mean squared prediction error? There are two possible points of comparison. First, the forecasting accuracy of an alternative model, estimated under different modeling assumptions or different estimation techniques, can be used for comparison purposes. Second, the out-of-sample accuracy measure can be compared to the same measure computed for the in-sample data points (that were used for parameter estimation) for which enough prior data values are available (that is, dropping the first _p_ data points, for which _p_ prior data points are not available). Since the model was estimated specifically to fit the in-sample points as well as possible, it will usually be the case that the out-of-sample predictive performance will be poorer than the in-sample predictive performance. But if the predictive quality deteriorates out-of-sample by "not very much" (which is not precisely definable), then the forecaster may be satisfied with the performance.

## See also\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=19 "Edit section: See also")\]

-   [Moving average model](https://en.wikipedia.org/wiki/Moving_average_model "Moving average model")
-   [Linear difference equation](https://en.wikipedia.org/wiki/Linear_difference_equation "Linear difference equation")
-   [Predictive analytics](https://en.wikipedia.org/wiki/Predictive_analytics "Predictive analytics")
-   [Linear predictive coding](https://en.wikipedia.org/wiki/Linear_predictive_coding "Linear predictive coding")
-   [Resonance](https://en.wikipedia.org/wiki/Resonance "Resonance")
-   [Levinson recursion](https://en.wikipedia.org/wiki/Levinson_recursion "Levinson recursion")
-   [Ornstein–Uhlenbeck process](https://en.wikipedia.org/wiki/Ornstein%E2%80%93Uhlenbeck_process "Ornstein–Uhlenbeck process")

## Notes\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=20 "Edit section: Notes")\]

1.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-1 "Jump up")** Shumway, Robert; Stoffer, David (2010). _Time series analysis and its applications : with R examples_ (3rd ed.). Springer. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [144197864X](https://en.wikipedia.org/wiki/Special:BookSources/144197864X "Special:BookSources/144197864X").
2.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-2 "Jump up")** Yule, G. Udny (1927) ["On a Method of Investigating Periodicities in Disturbed Series, with Special Reference to Wolfer's Sunspot Numbers"](http://visualiseur.bnf.fr/Visualiseur?Destination=Gallica&O=NUMM-56031), _[Philosophical Transactions of the Royal Society](https://en.wikipedia.org/wiki/Philosophical_Transactions_of_the_Royal_Society "Philosophical Transactions of the Royal Society") of London_, Ser. A, Vol. 226, 267–298.\]
3.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-3 "Jump up")** Walker, Gilbert (1931) ["On Periodicity in Series of Related Terms"](http://visualiseur.bnf.fr/Visualiseur?Destination=Gallica&O=NUMM-56224), _[Proceedings of the Royal Society](https://en.wikipedia.org/wiki/Proceedings_of_the_Royal_Society "Proceedings of the Royal Society") of London_, Ser. A, Vol. 131, 518–532.
4.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-4 "Jump up")** Theodoridis, Sergios (2015-04-10). "Chapter 1. Probability and Stochastic Processes". _Machine Learning: A Bayesian and Optimization Perspective_. Academic Press, 2015. pp. 9–51. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [978-0-12-801522-3](https://en.wikipedia.org/wiki/Special:BookSources/978-0-12-801522-3 "Special:BookSources/978-0-12-801522-3").
5.  ^ [Jump up to: _**a**_](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-Storch_5-0) [_**b**_](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-Storch_5-1) Von Storch, H.; F. W Zwiers (2001). _Statistical analysis in climate research_. Cambridge Univ Pr. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [0-521-01230-9](https://en.wikipedia.org/wiki/Special:BookSources/0-521-01230-9 "Special:BookSources/0-521-01230-9").\[_[page needed](https://en.wikipedia.org/wiki/Wikipedia:Citing_sources "Wikipedia:Citing sources")_\]
6.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-6 "Jump up")** Eshel, Gidon. ["The Yule Walker Equations for the AR Coefficients"](http://www-stat.wharton.upenn.edu/~steele/Courses/956/Resource/YWSourceFiles/YW-Eshel.pdf) (PDF). _stat.wharton.upenn.edu_.
7.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-Burg_7-0 "Jump up")** Burg, J. P. (1968). "A new analysis technique for time series data". In _Modern Spectrum Analysis_ (Edited by D. G. Childers), NATO Advanced Study Institute of Signal Processing with emphasis on Underwater Acoustics. IEEE Press, New York.
8.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-Brockwell_8-0 "Jump up")** Brockwell, Peter J.; Dahlhaus, Rainer; Trindade, A. Alexandre (2005). ["Modified Burg Algorithms for Multivariate Subset Autoregression"](https://web.archive.org/web/20121021015413/http://www3.stat.sinica.edu.tw/statistica/oldpdf/A15n112.pdf) (PDF). _Statistica Sinica_. **15**: 197–213. Archived from [the original](http://www3.stat.sinica.edu.tw/statistica/oldpdf/A15n112.pdf) (PDF) on 2012-10-21.
9.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-Burg1_9-0 "Jump up")** Burg, J.P. (1967) "Maximum Entropy Spectral Analysis", _Proceedings of the 37th Meeting of the Society of_ Exploration Geophysicists_, Oklahoma City, Oklahoma._
10.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-Bos_10-0 "Jump up")** Bos, R.; De Waele, S.; Broersen, P. M. T. (2002). ["Autoregressive spectral estimation by application of the burg algorithm to irregularly sampled data"](http://resolver.tudelft.nl/uuid:870559f7-f1e9-4968-83da-edd19485eaaf). _IEEE Transactions on Instrumentation and Measurement_. **51** (6): 1289. [doi](https://en.wikipedia.org/wiki/Doi_(identifier) "Doi (identifier)"):[10.1109/TIM.2002.808031](https://doi.org/10.1109%2FTIM.2002.808031).
11.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-11 "Jump up")** ["Fit Autoregressive Models to Time Series"](http://finzi.psych.upenn.edu/R/library/stats/html/ar.html) (in R)
12.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-12 "Jump up")** [Econometrics Toolbox Overview](http://www.mathworks.com/products/econometrics/)
13.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-13 "Jump up")** [System Identification Toolbox overview](http://www.mathworks.com/products/sysid/)
14.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-14 "Jump up")** ["Autoregressive modeling in MATLAB"](http://www.mathworks.com/help/econ/autoregressive-model.html)
15.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-15 "Jump up")** ["Time Series Analysis toolbox for Matlab and Octave"](http://pub.ist.ac.at/~schloegl/matlab/tsa/)
16.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-16 "Jump up")** [bayesloop: Probabilistic programming framework that facilitates objective model selection for time-varying parameter models.](https://github.com/christophmark/bayesloop)
17.  **[^](https://en.wikipedia.org/wiki/Autoregressive_model#cite_ref-17 "Jump up")** ["statsmodels.tsa.ar\_model.AutoReg — statsmodels 0.12.2 documentation"](https://www.statsmodels.org/stable/generated/statsmodels.tsa.ar_model.AutoReg.html). _www.statsmodels.org_. Retrieved 2021-04-29.

## References\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=21 "Edit section: References")\]

-   Mills, Terence C. (1990). [_Time Series Techniques for Economists_](https://archive.org/details/timeseriestechni0000mill). Cambridge University Press.
-   Percival, Donald B.; Walden, Andrew T. (1993). _Spectral Analysis for Physical Applications_. Cambridge University Press.
-   Pandit, Sudhakar M.; Wu, Shien-Ming (1983). _Time Series and System Analysis with Applications_. John Wiley & Sons.

## External links\[[edit](https://en.wikipedia.org/w/index.php?title=Autoregressive_model&action=edit&section=22 "Edit section: External links")\]

-   [AutoRegression Analysis (AR)](http://paulbourke.net/miscellaneous/ar/) by Paul Bourke
-   [Econometrics lecture (topic: Autoregressive models)](https://www.youtube.com/watch?v=b8yslhlIsA0&list=PLD15D38DC7AA3B737&index=8#t=34m25s) on [YouTube](https://en.wikipedia.org/wiki/YouTube "YouTube") by [Mark Thoma](https://en.wikipedia.org/wiki/Mark_Thoma "Mark Thoma")