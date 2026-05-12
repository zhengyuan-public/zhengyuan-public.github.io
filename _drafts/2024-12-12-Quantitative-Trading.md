---
comments: true
title: Quantitative Trading
date: 2024-12-12 12:00:00
image:
    path: /assets/img/images_preview/QuantitativeTradingPreview.jpg
math: true
categories: [Personal Notes and Collections, Quantitative Trading]
tags: [reading, finance, ernest-chan]
---

## The What, Who, and Why of Quantitative Trading

### Who

A few high school–level courses in math, statistics, computer programming, or economics,

- **Quantitative Trading** (**Quant**) is also known as **Algorithmic Trading**
- The kind of quant this book is about is called ***statistical arbitrage trading***.
- Most of individual quantitative traders, who were former institutional traders, are doing quite well on their own, while enjoying the **enormous freedom** that independence brings.
  - Gained some knowledge of finance,
  - Saved up a nest egg for the independent venture.
  - Prior appreciation of risks.
- **NO** need for immediate profits. Instant wealth is **NOT** the objective of quantitative trading.
- You should hope to have steadily increasing profits.
- Balance between **Fear** and **Greed**.

> "Make everything as simple as possible. But not simpler." — **Albert Einstein**
{: .prompt-tip }


The market is not stationary, most arbitrage opportunities eventually fade away.

### The Business Case of Quant

Starting a quant business is very similar to starting any small business.

**Scalability**

- Quant is very scalable (up to a point) because of the existence of ***leverage***.
  - Becoming a member of a proprietary trading firm allows you to use a much higher leverage.

**Time**

- How much time you need depends on the degree of **automation** you achieved.

**Non-necessity of Marketing**

- There is absolutely no marketing to do in a quantitative trading business. 
- ***You can focus exclusively on your product.*** To many people, this may be the ultimate beauty of starting your own quantitative trading business. 

### Fishing for Ideas

- Many strategies described by academics are either too complicated, out of date, or require expensive data to backtest.

- Try the multiple **variations** of a **basic strategy**.
- Start your own trading blog.
  - What truly makes a strategy proprietary and its secrets worth protecting are **the tricks and variations** that you have come up with, not the plain-vanilla version.
  - Bad ideas will quickly get shot down.
- The difficulty is not the lack of ideas. The difficulty is to **develop a taste** for which strategy is suitable for your personal circumstances and goals, and which ones look viable even before you devote the time to diligently backtest them.

### Identify Strategies that Suit You

- Working hours
  - Part-time: perhaps only strategies that hold overnight
- Programming Skills
- **Trading Capital**
  - What financial instruments and What strategies
  - (Retail Brokerage Account) or (Proprietary Trading Account)
    - With a low-capital account, you need to find strategies that can **maximize leverage** available.

### Your Goal

Maximum long-term growth is achieved by finding a strategy with the maximum Sharp Ratio, *provided that you have access to sufficiently high leverage*.

### A Taste for Strategies

#### Performance and Consistency

- Sharp Ratio

#### Transaction Cost

- Trading Frequency $$ \longrightarrow $$ Impact of Transaction Cost

#### Survivorship Bias

- A historical database of stock prices that does not include stocks that have disappeared due to bankruptcies, delistings, mergers, or acquisitions suffer from survivorship bias.
- Can **inflate** the historical performance of the strategy.
- Especially true if the strategy has a "value" bent: a tendency to buy cheat stocks.

#### Performance Changes

- Demand our model deliver good performance on recent data.

#### Data-Snooping Bias

- Overfitting $$ \longrightarrow $$ Fitting historical accident

> The key to successfully apply AI/ML to finance is to focus on **metalabeling** – i.e., finding the probability of profit of your own simple basic trading strategy, and **NOT** to use it to predict the market directly.
{: .prompt-tip }

## Backtesting

#### Look-Ahead Bias



## Mathematics

### Sharp Ratio

**Sharp Ratio** or a normalized measure of the return relative to its risk.
$$
r = \frac{\mathbb{E}[R]}{\sigma_R}
$$

- $$ R \Longrightarrow $$  **Excess Return = Portfolio Return - Benchmark Return**
- The benchmark is usually the market index (to which the securities you are trading belong).
- A rule of thumb
  - If $$ r < 1 $$, then the strategy is not suitable as a stand-alone strategy.
  - For a strategy with monthly profit, $$ r > 2 $$.
  - For a strategy with daily profit, $$ r > 3 $$.





## Glossary

### stock

### option

### security

### future

### foreign currency

### leverage

### buy/short (selling)

> When you **buy** a stock or asset, you're purchasing it with the expectation that its *value increases*. When you **short** a stock or asset, you are borrowing and selling it at the current market price, and then hoping its *value declines*.
{: .prompt-tip }

### long-short dollar-neutral

### regime shift

> Financial data from an earlier period simply cannot be fitted to the same model that is applicable today. Potential factors include changes in market regulation and macroeconomic events.
{: .prompt-tip }

### Exchange-Traded Fund (ETF)

### slippage

> The delay between the time your program *transmits* an order to your brokerage and the time it is *executed* at the exchange can cause a **slippage**.
{: .prompt-tip }

### market impact & capacity

> When you buy or sell a large chunk of securities, you will not be able to complete the transaction without impacting the prices. This effect on the market prices due to your own order is called **market impact**.  How much a strategy can absorb without negatively impacting its returns is called **Capacity**.
{: .prompt-tip }

## Words

|     Entry     |         IPA          |                  Meaning                   |
| :-----------: | :------------------: | :----------------------------------------: |
|   arbitrage   |    /ˈɑr bɪˌtrɑʒ/     |                  n. 套利                   |
|    lament     |      /ləˈmɛnt/       |                  n. 哀叹                   |
| discretionary |  /dəˈskreSHəˌnerē/   |               a. 自由决定的                |
|    divulge    |  / dɪˈvʌldʒ, daɪ- /  |                  vt. 泄露                  |
|   admonish    |    / ædˈmɒn ɪʃ /     |               vt. 告诫；警告               |
|  proprietary  | / prəˈpraɪ ɪˌtɛr i / | n. 所有权；独家商品<br />a. 专利的；专营的 |
|    allude     |                      |                                            |
|   parlance    |                      |                                            |
|   de facto    |                      |                                            |
|    merger     |                      |                                            |
