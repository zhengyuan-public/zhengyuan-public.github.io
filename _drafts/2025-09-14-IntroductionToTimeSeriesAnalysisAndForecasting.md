---
comments: true
title: Introduction to Time Series and Forcasting
date: 2025-09-14 12:00:00
image:
    path: /assets/img/images_time_series/time_series.jpeg
math: true
mermaid: true
categories: [Mathematics, Time Series Analysis]
tags: [mathematics, time-series-analysis]
---

## Quick Recapitulation

### Basics

For a random variable $$ X $$:

**Expectation/Mean**

$$ \mu = E[X] $$

**Variance/Volatility**

$$ Var(X) = \sigma^2 = E[(X- \mu)^2] = E[X^2] - E[X]^2 $$

**Covariance**

$$ Cov(X, Y) = E[(X-E[X])(Y-E[Y])] $$

---

## Introduction to Forecasting

> A forecast is a prediction of some future event or events.
{:.prompt-tip}

Historical data usually exhibit inertia and do not change dramatically very quickly, statistical methods are very useful for short- and medium-term forecasting.

A time series is a time-oriented or chronological sequence of observations on a variable of interest.

### Qualitative Methods

1. Qualitative forecasting techniques are often subjective in nature and require judgment on the part of experts.
2. There is little or no historical data on which to base the forecast.

> **Delphi Method** developed by the RAND Corporation
{:.prompt-tip}

### Quantitative Methods

1. Quantitative forecasting techniques make formal use of historical data and a forecasting model.

2. Three types of models
   - **Regression Models**: The predictor variables are assumed to describe the forces that cause or drive the observed values of the variable of interest.

   - **Smoothing Models**: Employ a simple function of previous observations to provide a forecast of the variable of interest. Pros: formal statistical basis; Cons: often used and justified heuristically on the basis that they are easy to use.

   - **General Time-series Models**: employ the statistical properties of the historical data to specify a formal model and then estimate the unknown parameters of this model.

3. The form of prediction
   - Point estimate/forecast 
   - Prediction Interval
4. Forecast horizon (a.k.a. forecast lead time) is the number of future periods for which forecasts must be produced.
5. Forecast interval is the frequency with which new forecasts are prepared.

### Time-Series Examples

Some patterns

1. Random
2. Trends
3. Level Shifts
4. Periods or Cycles
5. Unusual observations
6. Combination of above patterns

Due to the continuous nature, some properties are **positively autocorrelated** where a value above the long-run average tends to be followed by other values above the average, while a value below the average tends to be followed by other values below the average.

Business data such as stock prices and interest rates often exhibit non-stationary behavior; that is, the time series has no natural means. While the price is constant in some short time periods, there is no consistent mean level over time.

### Forecasting Process

1. Problem definition
2. Data collection
3. Data analysis
4. Model selection and fitting
5. Model validation
6. Forecasting model development
7. Monitoring forecasting model performance

**Problem definition**: how the forecast will be used along with the expectations of the “customer”. 

- Form of the forecast
- Forecast horizon
- Forecast interval
- Forecast accuracy

## Statistics Background for Forecasting

### Basics

#### Forecast/Predicted Value 

The predicted value is the estimate (made at $$ (t - \tau) $$) of the response variable ($$ \hat{y}_t(t-\tau) $$) that a model generates for **new, future, or out-of-sample data**.

#### Fitted Value

The fitted value is the estimate of the response variable $$ (\hat{y}_t) $$ that a model generates for the **historical data** (the in-sample data) that was used to train or "fit" the model.

#### Lead - $$ \tau $$ Forecast Errors

$$
e_t(\tau) = y_t - \hat{y}_t(t - \tau) \nonumber
$$

#### Residuals

$$
e_t = y_t - \hat{y}_t \nonumber
$$

>  $$ e_t $$ is almost always smaller than $$ e_t(\tau) $$
{:.prompt-tip}

### Graphical Displays

Plotting Originial Data

Plotting Smoothed Data

### Numerical Descriptions

#### Stationarity

##### Strictly Stationary 

For each $$ k, t, n $$, the distribution $$ \{y_t, \dots, y_{t+k}\} $$ is the same as $$ \{y_{t+n}, \dots, y_{t+k+n}\} $$.

##### (2nd Order) Stationary 

1. The mean $$ E[y_t] $$ does **NOT** depend on $$ t $$;
2. The **second moment** $$ E[y_t^2] $$ does **NOT** depend on $$ t $$ (PS: $$ Var(y_t) = E[y_t^2] - E[y_t]^2 $$);
3. The autocovariance $$ Cov(y_t, y_{t+k}) $$ does **NOT** depend on $$ t $$ (PS: only depends on $$ k $$).

> Also known as: **weak-sense stationarity**, **wide-sense stationarity (WSS)**, or **covariance stationarity**.
{:.prompt-tip}

##### White Noise $$ \{e_t\}$$ 

1. Zero mean: $$ E[e_t] = 0 $$;
2. Constant variance: $$ E[e_t^2] = \sigma^2 \Longleftarrow Var(e^t) = E[e_t^2] - E[e_t]^2 = E[e_t^2] - 0 = \sigma^2 $$;
3. Zero correlation over time: $$ E[e_t e_s] =0, \forall t \neq s $$.

#### Autocorrelation Function

##### Autocovariance at lag $$ k $$

- Scatter plot of $$ y_t - y_{t+k}$$ can be used for visualization;
- \$$ \gamma_k = Cov(y_t, y_{t+k}) = E[(y_{t} - \mu)(y_{t+k} - \mu)] $$ 

##### Autocovariance Function at lag $$ k $$

$$
ACovF(k) = \{\gamma_k\}, k=0, 1, 2, \dots \nonumber
$$

##### Autocorrelation Coefficient at lag $$ k $$

$$
\rho_k = \frac{E[(y_{t} - \mu)(y_{t+k} - \mu)]}{\sqrt{E[(y_{t} - \mu)^2]E[(y_{t+k} - \mu)^2]}} = \frac{Cov(y_t, y_{t+k})}{Var(y_t)} = \frac{\gamma_k}{\gamma_0} \nonumber
$$

##### ACF (Autocorrelation Function)

$$
ACF(k)= \{\rho_k\}, k=0, 1, 2, \dots \nonumber
$$

- \$$ \rho_0 = 1 $$
- ACF is a dimensionless quantity
- ACF is symmetric around zero: $$ \rho_{k} = \rho_{-k} $$

> If a time series has a finite mean and ACF, it is said to be **2nd-order Stationary**. If, in addition, the *joint probability distribution* of the observations at all times is *multivariate normal*, then it is **Strictly Stationary**.
{:.prompt-info}

##### Sample(Estimate) ACF

- Estimate autocovariance from a finite time series $$ \{ y_1, y_2, \dots, y_T\} $$

$$
\hat{\gamma}_k = \frac{1}{T}\sum_{t=1}^{T-k}, k=0, 1, 2, \dots, K \nonumber
$$

- Estimate ACF

$$
\hat{\rho_k} = \frac{\hat{\gamma}_k}{\hat{\gamma}_0},  k=0, 1, 2, \dots, K \nonumber
$$

- General rule of thumb
   1. At least 50 observations are required to have a good estimate of ACF;
   2. $$ K $$ should be about $$ T/4 $$;
   3. It is often needed to determine *if the autocorrelation coefficient at a particular lag is zero  is zero*, which can be done by comparing the **Sample Autocorrelation Coefficient** to its **Standard Error**.

> It is often needed to determine if the autocorrelation coefficient at a particular lag is zero because this determination is **fundamental for understanding the underlying structure of a time series and for the proper specification of statistical models**, particularly in time series analysis and regression.
> 
> **Identifying Data Structure and Randomness**
> 
> Testing whether the autocorrelation is significantly different from zero directly addresses whether the current value of a time series has a **linear dependence** on its past values at that specific time lag.
> - **Randomness (White Noise):** If the true autocorrelation coefficient $$ \rho_k $$ is zero for all lags $$ k>0 $$, the time series is considered **white noise** (a purely random process). Statistical analysis and forecasting for a white noise series are simplified, as each observation is independent of the others.
> - **Presence of Patterns:** A coefficient **significantly different from zero** at lag k indicates that there is a **linear pattern or memory** in the data separated by k time periods. For example:
>   - A significant spike at **lag 1** suggests the current value is directly related to the immediately preceding value (a common phenomenon in many time series).  
>   - Significant spikes at **lag 12** in monthly data suggest a **seasonal pattern** (e.g., sales in December are correlated with sales in the previous December). 
>
> **Time Series Model Selection**
>
> The autocorrelation function (ACF) and partial autocorrelation function (PACF), which plot the autocorrelation coefficients against the lag k, are the **primary tools** for identifying the appropriate order and components of **ARIMA (Autoregressive Integrated Moving Average)** and other time series models.
> - **Autoregressive (AR) Models:** A significant partial autocorrelation at lag $$ p $$ (with near-zero partial autocorrelations for lags $$ >p $$) is used to determine the order (p) of an autoregressive component, **AR(p)**.
> - **Moving Average (MA) Models:** A significant autocorrelation at lag $$ q $$ (with near-zero autocorrelations for lags $$ >q $$) is used to determine the order (q) of a moving average component, **MA(q)**.
>
> **Model Adequacy and Residual Analysis**
>
> After fitting a statistical model (like linear regression or an ARIMA model), the assumption is often that the **errors (residuals)** of the model are **independent** and therefore exhibit no remaining autocorrelation (i.e., they should resemble white noise).
>
> - **Testing Model Fit:** If the **residuals** of a fitted model show a significant autocorrelation at a particular lag, it means the model has **failed to capture a pattern** in the original data. This indicates the model is **mis-specified** or **inadequate**, and it needs to be revised (e.g., by including more lagged terms or a different model structure). 
> - **Valid Inference:** The assumption of independent errors is crucial for many statistical inference procedures (e.g., calculating standard errors, p-values, and confidence intervals). If significant autocorrelation exists in the errors, these measures can be **biased or misleading**, leading to incorrect conclusions about the significance of model parameters.
{:.prompt-info}

##### The Variogram

$$
G_k = \frac{Var(y_{t+k} - y_t)}{Var(y_{t+1} - y_t)}, k = 1, 2, \dots \nonumber \xrightarrow[]{\text{ If stationary }} \frac{1 - \rho_k}{1 - \rho_1}, k = 1, 2, \dots \nonumber
$$

- For stationary time series $$ \displaystyle\lim_{k \to \infty} \rho_k = 0 $$, so $$ \displaystyle\lim_{k \to \infty} G_k = \frac{1}{1 - \rho_1} $$
- For non-stationary time series, $$ G_k $$ will increase monotonically

### Data Transformations and Adjustments

> Data Transformations are often used for stabilizing the variance of the data.
{:.prompt-tip}

#### Power Family of Transformation

$$
y^{(\lambda)}=
\begin{cases}
		\displaystyle\frac{y^{\lambda} - 1}{\lambda \dot{y}^{(\lambda - 1)}}, \lambda \neq 0 \\
    \displaystyle\dot{y} \ln y, \lambda = 0 \\ 
\end{cases}
\text{ where } \dot{y} = \exp[\frac{1}{T}\sum_{t=1}^T \ln y_t] = \textstyle\sqrt[T]{\prod_{t=1}^{T}y_t} \nonumber
$$

> $$ \dot{y} $$ is the geometric mean and $$ \lambda \dot{y}^{(\lambda - 1)} $$ is a scale factor to ensure the **Residual Sum of Squares**  ($$ \displaystyle RSS = \sum_{i=1}^n (y_i - \hat{y_i})^2 $$) are comparable for different fitted models. $$ \lambda $$ is typically chosen empirically by testing different values and selecting the one with minimum RSS.
{:.prompt-tip}

1. Square Root Transformation $$ \lambda = 0.5 $$

2. Reciprocal Square Root Transformation $$ \lambda = -0.5 $$

3. Inverse Transformation $$ \lambda = -1 $$

4. Log Transformation $$ \lambda = 0 $$

   - Often used when the variance increases with the mean of the time series (Optimal when the **STD** increases linearly with the **Mean**).

   - Physical interpretation as **percentage change**.


#### Trend Adjustments

1. Decompose the time series into trend and non-trend component, and fit a regression model describing the trend component.
2. Differencing the data to obtain a new time series.

#### Seasonal Adjustments

1. Differencing can also be used to eliminate seasonality.
