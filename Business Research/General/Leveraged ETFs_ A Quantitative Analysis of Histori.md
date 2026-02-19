# Leveraged ETFs: A Quantitative Analysis of Historical Performance and Volatility Decay

## Executive Summary

This report provides a comprehensive, data-driven analysis of Leveraged Exchange-Traded Funds (LETFs), sophisticated financial instruments designed to amplify market returns. A leveraged ETF is an exchange-traded fund engineered to deliver a multiple—such as two times (2x) or three times (3x)—of the **daily** performance of a specific underlying index.

This analysis focuses on two of the most popular and volatile examples:

1.  **ProShares UltraPro QQQ (TQQQ):** Seeks 3x the *daily* return of the Nasdaq-100 Index.

2.  **ProShares UltraPro Short QQQ (SQQQ):** Seeks -3x the *daily* (inverse) return of the Nasdaq-100 Index.

The central thesis of this report, supported by extensive historical data and academic analysis, is that the "daily" objective of these funds is a structural mechanism that leads to **path-dependent returns**. This mechanism, known as "volatility decay" or "variance drain," causes a LETF's long-term performance to diverge significantly from its stated multiple of the index's cumulative return.

This quantitative review will demonstrate:

-   In **strong, trending bull markets** (e.g., 2020-2021), the daily compounding effect can work favorably, though returns are not a simple 3x multiple.

-   In **sharp bear markets** (e.g., 2022), the leverage magnifies losses to a catastrophic degree.

-   In **volatile, sideways markets** (e.g., 2015, 2018), volatility decay creates a "lose-lose" scenario, where *both* the bull (TQQQ) and bear (SQQQ) funds can lose significant value, even if the underlying index finishes flat.

We conclude that LETFs are unsuitable for buy-and-hold investors. They are high-risk, short-term *trading instruments* designed exclusively for sophisticated traders who intend to actively monitor their positions on a daily basis.

## 1. The Core Mechanism: Daily Resets and Derivatives

To understand their performance, one must first understand their mechanics. Unlike a traditional ETF (like QQQ), TQQQ and SQQQ do not primarily hold stocks. Instead, they use a portfolio of financial derivatives—primarily **swap agreements** and **futures contracts**—to achieve their target leverage.

The fund's assets are held as collateral (often U.S. Treasury Bills) for these swap contracts with large investment banks (counterparties). This derivative-based structure is essential for achieving a notional exposure that is 3x (or -3x) the fund's net assets.

### 1.1 The "Daily Reset"

To maintain this precise leverage ratio, the fund *must* rebalance its exposure at the end of every trading day. This "daily reset" is the engine of path-dependent returns:

-   **If the Index Rises:** TQQQ's value increases. To maintain a 3x leverage ratio on this new, larger asset base, the fund manager is forced to *buy more* derivatives (i.e., add more long exposure).

-   **If the Index Falls:** TQQQ's value decreases. To avoid becoming *over-leveraged* relative to its new, smaller asset base, the fund manager is forced to *sell* derivatives (i.e., reduce long exposure).

This creates a forced, pro-cyclical trading strategy: the fund automatically "buys high" and "sells low" every single day. This mechanical behavior is the primary source of volatility decay.

## 2. The Primary Disadvantage: A Quantitative Analysis of Volatility Decay

Volatility decay (or variance drain) is the mathematical erosion of a LETF's value over time, driven by the compounding of daily leveraged returns.

### 2.1 A Simple Mathematical Example

Consider a hypothetical two-day period where the underlying index starts at 100, rises 10% on Day 1, and then falls 9.09% on Day 2, returning perfectly to 100.

| Instrument      | Start Value | Day 1: Index +10% | Day 2: Index -9.09% | End Value | Net Return  |
|-----------------|-------------|-------------------|---------------------|-----------|-------------|
| 1x Index (QQQ)  | $100.00     | $110.00           | $100.00             | $100.00   | **0.00%**   |
| 3x Bull (TQQQ)  | $100.00     | $130.00           | $94.55              | $94.55    | **-5.45%**  |
| -3x Bear (SQQQ) | $100.00     | $70.00            | $89.09              | $89.09    | **-10.91%** |

**How this happens:**

-   **TQQQ:** On Day 1, it gains 30% (100 \\rightarrow 130). On Day 2, the index falls 9.09%, so TQQQ must fall 3 \\times -9.09\\% = -27.27\\%. This loss is calculated from its *new, higher* value: $130 \\times (1 - 0.2727) = 94.55.

-   **SQQQ:** On Day 1, it loses 30% (100 \\rightarrow 70). On Day 2, the index falls 9.09%, so SQQQ must *gain* -3 \\times -9.09\\% = +27.27\\%. This gain is calculated from its *new, lower* value: $70 \\times (1 + 0.2727) = 89.09.

This example proves a critical concept: in a volatile, "choppy" market that ends flat, **both the bull and bear LETFs lose significant value**.

### 2.2 Academic & Regression Findings

Academic studies confirm that LETF returns are "path-dependent". This means the *path* the index takes (a smooth trend vs. a volatile, choppy ride) is more important than its final destination for the LETF's long-term return.

-   **Key Variables:** Regression analyses performed in financial journals identify volatility as the primary driver of decay. The performance of a LETF is a function of leverage, time, index return, and volatility.

-   **Market Regimes:** Studies confirm that daily-rebalanced LETFs (like TQQQ) are optimized for momentum-driven, trending markets. In these regimes, the "buy high" mechanism positively compounds returns. Conversely, in mean-reverting or sideways markets, this same mechanism erodes returns, and less-frequent rebalancing (e.g., weekly) would be less destructive.

-   **Long-Term Unsuitability:** The consensus from academic analysis is that the need for dynamic rebalancing and the path-dependent nature of returns make LETFs, as currently designed, unsuitable for buy-and-hold investors.

## 3. Real-World Performance: Historical Case Studies

The "daily reset" mechanism creates dramatically different outcomes depending on the market regime. The following case studies of TQQQ, SQQQ, and their underlying index (represented by QQQ) use real, full-year historical data.

### Case Study 1: The 2022 Bear Market (Amplified Losses)

2022 was a devastating bear market for technology stocks. This environment demonstrates the catastrophic downside of leverage.

| Ticker   | Instrument    | 2022 Calendar Year Return | Max Drawdown           |
|----------|---------------|---------------------------|------------------------|
| **QQQ**  | 1x Nasdaq-100 | **-32.58%**               | \~-35.1%               |
| **TQQQ** | 3x Bull       | **-80.36%**               | **-81.7%**             |
| **SQQQ** | -3x Bear      | **+82.36%**               | N/A (Fund appreciated) |

-   **Analysis:** TQQQ's loss (-80.36\\%) was *not* simply 3x the index's loss (3 \\times -32.58\\% = -97.74\\%). The daily rebalancing in a volatile downtrend meant the fund was forced to "sell low" day after day, locking in losses, which paradoxically *prevented* it from going to zero but still resulted in a catastrophic loss of capital. An investor who held TQQQ through 2022 would need a **+400% gain** just to break even.

### Case Study 2: The 2020-2021 Bull Market (Positive Compounding)

The post-COVID bull market was a strong, low-volatility trend, the ideal environment for a "bull" LETF.

| Ticker   | Instrument    | 2020 Return | 2021 Return |
|----------|---------------|-------------|-------------|
| **QQQ**  | 1x Nasdaq-100 | +48.62%     | +27.42%     |
| **TQQQ** | 3x Bull       | +110.05%    | +82.98%     |

-   **Analysis:** In this regime, the "buy high" daily reset mechanism was consistently rewarded.

    -   In 2021, a strong, steady year, TQQQ's return (+82.98\\%) was slightly *better than* 3x the QQQ's return (3 \\times 27.42\\% = 82.26\\%). This is the "compounding boost" in action.

    -   In 2020, TQQQ returned "only" 2.26x the index (110.05 / 48.62). This is because 2020, while finishing strong, included the massive volatility and crash of March 2020, which caused significant volatility decay that the subsequent rally could not fully overcome. This demonstrates that *even in a positive year, volatility is a drag*.

### Case Study 3: The 2015 & 2018 Sideways Markets (Volatility Decay)

These two years provide the clearest real-world evidence of volatility decay and the "lose-lose" scenario.

| Year     | Ticker | Instrument    | Index Return (Nasdaq-100) | ETF Annual Return |
|----------|--------|---------------|---------------------------|-------------------|
| **2015** | QQQ    | 1x Nasdaq-100 | **+8.43%**                | **+9.45%**        |
|          | TQQQ   | 3x Bull       | +8.43%                    | **+17.23%**       |
|          | SQQQ   | -3x Bear      | +8.43%                    | **-37.50%**       |
|          |        |               |                           |                   |
| **2018** | QQQ    | 1x Nasdaq-100 | **-1.04%**                | **-0.13%**        |
|          | TQQQ   | 3x Bull       | -1.04%                    | **-21.27%**       |
|          | SQQQ   | -3x Bear      | -1.04%                    | **-20.74%**       |

-   **Analysis (2015):** The index was modestly positive (+8.43\\%). TQQQ returned only \~2x this amount, not 3x. SQQQ, which bets against the index, *should* have lost 3 \\times 8.43\\% = 25.29\\%. Instead, it lost a staggering **37.50%**. The volatility of the year "decayed" its value.

-   **Analysis (2018):** This is the definitive case study. The index was **perfectly flat** (\~ -1\\%). A buy-and-hold investor in QQQ broke even. However, an investor holding TQQQ *lost 21%*. An investor holding SQQQ *also lost 21%*. This is the direct, real-world consequence of the mathematical example in Section 2.1. In a choppy, directionless market, *everyone* holding a daily-reset LETF loses.

## 4. Simulated & Early Historical Performance (Pre-Inception Analysis)

To address performance in earlier crises, we must use a combination of actual early data and simulated back-tests. TQQQ and SQQQ were both launched on **February 9, 2010**. Any performance data before this date is hypothetical, based on simulating the 3x daily rebalancing mechanism against the historical returns of the Nasdaq-100 index.

### 4.1 Case Study: The 2010 Inception Year (Actual Data)

The funds launched in the midst of a strong recovery from the 2008 crisis. This represents a real-world, high-momentum, trending market.

| Ticker   | Instrument    | 2010 Calendar Year Return |
|----------|---------------|---------------------------|
| **QQQ**  | 1x Nasdaq-100 | **+19.91%**               |
| **TQQQ** | 3x Bull       | **+76.05%**               |
| **SQQQ** | -3x Bear      | **-21.22%**               |

-   **Analysis:** In its first (partial) year, TQQQ returned **3.8x** the performance of QQQ, not 3x. This is a clear, real-world example of the "compounding boost." The strong, trending recovery with relatively low volatility allowed the "buy high" daily reset mechanism to work in the fund's favor, amplifying long-term returns beyond the stated daily multiple.

### 4.2 Case Study (Simulated): The 2007-2008 Global Financial Crisis (GFC)

This period was characterized by a sharp, systemic crash. Back-testing a hypothetical TQQQ reveals the severity of leveraged drawdowns.

\| Year \| Ticker \| Instrument \| Annual Return \| \| :--- \| :--- \| :---: \| \| **2007** \| QQQ \| 1x Nasdaq-100 \| **+18.67%** \| \| **2008** \| QQQ \| 1x Nasdaq-100 \| **-41.89%** \|

-   **Simulated TQQQ Performance:** A back-test of a hypothetical TQQQ starting in 2006 shows it would have suffered a **-90% drawdown** during the 2008 crisis. A simulation starting at the absolute *peak* before the 2008 crisis shows a **-96% drawdown**.

-   **Analysis:** A 96% loss requires a **+2,400% gain** just to break even. Simulations show that this hypothetical TQQQ would have taken *three years longer* than QQQ to recover its previous peak. This illustrates the "constant leverage trap": the fund's asset base is so decimated by the crash that it has little capital left to participate in the recovery.

### 4.3 Case Study (Simulated): The 2000-2002 Dot-Com Bubble

This is the ultimate stress test for a technology-focused leveraged fund. The Nasdaq-100 index experienced a multi-year crash, falling over 80% from its peak.

\| Year \| Ticker \| Instrument \| Annual Return \| \| :--- \| :--- \| :---: \| \| **2000** \| QQQ \| 1x Nasdaq-100 \| **-36.84%** \| \| **2001** \| QQQ \| 1x Nasdaq-100 \| **-32.65%** \| \| **2002** \| QQQ \| 1x Nasdaq-100 \| **-37.58%** \|

-   **Simulated TQQQ Performance:** A hypothetical TQQQ would have been **"completely obliterated"**. A simulated 2x (let alone 3x) leveraged fund on a similar tech stock (Intel) that crashed 80% would have resulted in a **-99% loss**.

-   **Analysis:** This is the "zone of no return". A back-test starting in January 2000, just before the crash, shows that the hypothetical TQQQ would *still* be **down 70%** from its starting value two decades later (as of 2020). The fund's value would have been permanently impaired, never recovering even as the underlying index eventually did.

### 4.4 Case Study (Simulated): The 1970s and 1980s

Analyzing these decades requires using the Nasdaq Composite (data from 1971) and the Nasdaq-100 (data from 1985) as proxies.

-   **1970s (Stagflation):** This period saw high inflation, high interest rates, and a severe bear market. From 1973-1974, the Nasdaq Composite **plunged 59%**. A hypothetical 3x leveraged fund would have suffered a catastrophic, near-total loss, similar to the 2000 crash. Furthermore, the high-interest-rate environment would have dramatically increased the fund's internal borrowing and swap costs, creating a significant performance drag not captured in simple back-tests.

-   **1980s (Bull Market):** Following the early 80s recession, the Nasdaq-100 (from 1985) entered a strong, trending bull market.

    -   **1986:** +6.89%

    -   **1987:** +10.50%

    -   **1988:** +13.54%

    -   **1989:** +26.17%

-   **Analysis:** This low-volatility, high-momentum regime is the *ideal* environment for a leveraged bull fund. A hypothetical TQQQ would have performed exceptionally well, benefiting from the "compounding boost" much as it did in the 2010s.

## 5. Advantages and Disadvantages (Revisited)

| Advantages                                                                                                                                                                  | Disadvantages                                                                                                                                                                                                                                                 |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Magnified Short-Term Gains:** The primary allure. A correct *1-day* directional call is amplified by 3x.                                                                  | **Magnified, Catastrophic Losses:** Leverage is a double-edged sword. As the 2022 and simulated 2000/2008 case studies show, drawdowns are rapid, severe (&gt;-90%), and can be permanent.                                                                    |
| **Capital Efficiency:** A trader can gain 30,000 of notional exposure with only 10,000 of capital, freeing up cash for other uses.                                          | **Volatility Decay:** As the 2018 case study proves, these funds are structurally designed to lose value in choppy, sideways markets.                                                                                                                         |
| **Accessibility & Hedging:** Inverse funds (SQQQ) provide a simple way to profit from downturns or hedge a portfolio without a margin account or options/futures knowledge. | **High Expense Ratios:** These are costly products. TQQQ's expense ratio is \~0.82-0.97% and SQQQ's is \~0.95% , versus \~0.20% for QQQ. These high fees are a constant drag on performance.                                                                  |
|                                                                                                                                                                             | **Tax Inefficiency:** The fund's constant daily rebalancing of its derivative portfolio can generate a high volume of short-term capital gains, which are passed on to investors.                                                                             |
|                                                                                                                                                                             | **Counterparty Risk:** The fund's value is dependent on counterparties (investment banks) making good on their swap agreements. In a systemic financial crisis, a counterparty failure could render the ETF valueless, regardless of the index's performance. |

---

## 6. The Hedging Conundrum: Can LETFs Be Used for Hedging?

Yes, but only as a **tactical, short-term tool**, not a strategic, long-term hedge.

A portfolio manager who owns 3,000,000 of QQQ but fears a sharp, short-term drop (e.g., over a few days) could buy 1,000,000 of SQQQ. This is more capital-efficient than shorting 3,000,000 of stock or buying 3,000,000 of a -1x fund. If the market drops 2% that day, the QQQ position loses 60,000, while the SQQQ position gains \~60,000 (1M \\times 6\\%), creating a temporary, capital-efficient hedge.

**The Problem:** This hedge is a "melting ice cube". As the 2018 case study demonstrated, SQQQ loses value over time if the market is choppy or flat. If the manager holds that SQQQ "hedge" for a year and the market ends flat, their main portfolio is unchanged, but their hedge has *lost 20%* of its value.

Academic research confirms this. Holding inverse funds passively is ineffective due to decay. Effective hedging strategies using LETFs are *dynamic* and *signal-based* (e.g., adding an SQQQ hedge only when the index breaks a 200-day moving average). This is a complex, active trading strategy, unlike buying a protective put option, which provides a defined hedge for a set period.

\#\# 7. Conclusion: The Ideal Situation and Investor Profile

The quantitative, real-world data leads to an unequivocal conclusion.

**1. In which situation is best for investing in them?** The word "investing" (implying a long-term hold) is a dangerous misnomer. These are unsuitable for long-term investors, a fact stated repeatedly by financial regulators like the SEC and FINRA.

The optimal *trading* scenario for a **bull fund (TQQQ)** is a **strong, high-momentum, low-volatility uptrend** (like 2021 or the 1980s simulation).

The optimal *trading* scenario for a **bear fund (SQQQ)** is a **strong, high-momentum, low-volatility downtrend** (like 2022).

The *worst possible situation* for *both* funds is a **volatile, choppy, sideways market** (like 2018), where volatility decay erodes value from all sides. The *absolute worst* outcome is a multi-year crash (like 2000-2002), which leads to permanent, irrecoverable losses.

**2. Who is the ideal user?** The ideal user is *not* a retail investor. The ideal user is a **sophisticated, active, short-term trader** who:

-   Fully understands the mathematics of path-dependency and volatility decay.

-   Has a strong, high-conviction directional thesis for the next 1-3 trading sessions *only*.

-   Intends to actively monitor and manage the position on a daily, if not hourly, basis.

For 99% of investors, the answer is simple: the complexity, fees, and decay risk of LETFs far outweigh their speculative allure.

#### Works cited

1\. Updated Investor Bulletin: Leveraged and Inverse ETFs, https://www.investor.gov/introduction-investing/general-resources/news-alerts/alerts-bulletins/investor-alerts/sec 2. Leveraged ETFs - Fidelity Investments, https://www.fidelity.com/learning-center/investment-products/etf/types-of-etfs-leveraged-etfs 3. What are Leveraged ETFs and how do they work? - IG Group, https://www.ig.com/en/trading-strategies/leveraged-etfs--what-are-they-and-how-do-they-work--230605 4. TQQQ: The World's Largest Leveraged ETF - ProShares, https://www.proshares.com/browse-all-insights/insights/tqqq-the-worlds-largest-leveraged-etf 5. TQQQ \| UltraPro QQQ - ProShares, https://www.proshares.com/our-etfs/leveraged-and-inverse/tqqq 6. SUMMARY PROSPECTUS - UltraPro QQQ - ProShares, https://www.proshares.com/globalassets/proshares/prospectuses/tqqq\_summary\_prospectus.pdf 7. ProShares UltraPro QQQ: TQQQ Stock Price Quote & News - Robinhood, https://robinhood.com/us/en/stocks/TQQQ/ 8. ProShares UltraPro QQQ, https://www.schwab.wallst.com/schwab/Prospect/research/etfs/reports/reportRetrieve.asp?reportType=etfrc&symbol=TQQQ 9. ProShares Fact Sheet \| TQQQ, https://www.proshares.com/globalassets/proshares/fact-sheet/prosharesfactsheettqqq.pdf 10. SQQQ \| UltraPro Short QQQ - ProShares, https://www.proshares.com/our-etfs/leveraged-and-inverse/sqqq 11. QQQ vs SQQQ \| ETF Performance Comparison Tool - Composer.trade, https://www.composer.trade/etf-comparisons/QQQ-SQQQ 12. proshares ultrapro short qqq - SEC.gov, https://www.sec.gov/Archives/edgar/data/1174610/000119312518287997/d620881d497k.htm 13. ProShares UltraPro Short QQQ, https://www.schwab.wallst.com/schwab/Prospect/research/etfs/reports/reportRetrieve.asp?reportType=etfrc&symbol=SQQQ 14. ProShares Fact Sheet \| SQQQ, https://www.proshares.com/globalassets/proshares/fact-sheet/prosharesfactsheetsqqq.pdf 15. ProShares UltraPro Short QQQ SQQQ ETF Summary Overview - Morningstar Canada, https://global.morningstar.com/en-ca/investments/etfs/0P0000IMT2/quote 16. SUMMARY PROSPECTUS - UltraPro Short QQQ - ProShares, https://www.proshares.com/globalassets/proshares/prospectuses/sqqq\_summary\_prospectus.pdf 17. Compounding Effects in Leveraged ETFs: Beyond the Volatility Drag ParadigmThis manuscript is a preprint and is currently under review for publication. - arXiv, https://arxiv.org/html/2504.20116v1 18. Path-dependence properties of leveraged exchange-traded funds: Compounding, volatility and option pricing - ProQuest, https://search.proquest.com/openview/71803f0000a65f6c544d9b2874e4d644/1?pq-origsite=gscholar&cbl=18750 19. Understanding the Perils (and Potential) of Leveraged ETFs - GSR Markets, https://www.gsr.io/insights/reports-understanding-the-perils-and-potential-of-leveraged-etfs 20. TQQQ vs. QQQ: What's the Difference? - Investopedia, https://www.investopedia.com/investing/qqq-vs-tqqq-difference-and-which-better/ 21. Leveraged ETFs Explained: How They Work, Risks, and Benefits \| LeverageSharesUS, https://leverageshares.com/us/insights/leveraged-etfs-explained-how-they-work-risks-and-benefits/ 22. Daily Reset, Long-Term Risk: Why Leveraged ETFs Aren't Built for Buy-and-Hold - Minnesota Valley Grain -, https://www.mnvalleygrain.com/news/story/35838311/daily-reset-long-term-risk-why-leveraged-etfs-aren-t-built-for-buy-and-hold 23. Risks of Complex Registered Funds \| JP Morgan, https://www.jpmorgan.com/content/dam/jpm/securities/documents/investing-in-non-traditional-funds.pdf 24. Path-Dependence of Leveraged ETF Returns \| SIAM Journal on Financial Mathematics, https://epubs.siam.org/doi/10.1137/090760805 25. The flaw in the Leveraged ETF argument, https://www.reddit.com/r/Bogleheads/comments/1ns3f0o/the\_flaw\_in\_the\_leveraged\_etf\_argument/ 26. Adviser Alert: Inverse and Leveraged ETFs \| DORA - Colorado Division of Securities, https://securities.colorado.gov/press-release/adviser-alert-inverse-and-leveraged-etfs 27. Regulatory Notice 09-31 \| FINRA.org, https://www.finra.org/rules-guidance/notices/09-31 28. Opportunities in Leveraged ETFs - Tradier Hub, https://hub.tradier.com/articles/leveraged-etfs/ 29. Smart ways to use leveraged ETFs to supercharge your portfolio - YouTube, https://www.youtube.com/watch?v=FVqIvrs0wps 30. TQQQ Profile - ETF Guide - SumGrowth, https://www.sumgrowth.com/etf-profile/invest-in-TQQQ-etf.html 31. Understanding Leveraged & Inverse Exchange Traded Funds - Direxion, https://www.direxion.com/education/understanding-leveraged-exchange-traded-funds 32. TQQQ: Read This First Before Leveraging The Nasdaq-100 For 3x Potential Returns, https://seekingalpha.com/article/4787742-tqqq-read-this-first-before-leveraging-the-nasdaq-100-for-3x-potential-returns 33. Why Do Leveraged ETFs Decay? Understanding the Mechanics and Risks, https://www.crystalfunds.com/insights/leveraged-etfs-decay-understanding-mechanics-and-risks 34. Leveraged ETFs: Amplifying Gains or Risks? - ArchBridge Family Office, https://archbridge.com/insights/leveraged-etfs-amplifying-gains-or-risks/ 35. Leveraged Investing Strategies – Know the Risks Before Using These Advanced Investment Tools \| Investor.gov, https://www.investor.gov/introduction-investing/general-resources/news-alerts/alerts-bulletins/investor-bulletins/leveraged-investing-strategies-know-risks-using-these-advanced-investment-tools 36. Can someone explain what a leveraged ETF is and how it works? : r/investing - Reddit, https://www.reddit.com/r/investing/comments/1m4uois/can\_someone\_explain\_what\_a\_leveraged\_etf\_is\_and/ 37. Derivative (finance) - Wikipedia, https://en.wikipedia.org/wiki/Derivative\_(finance) 38. ProShares UltraPro Short QQQ SQQQ ETF Portfolio Review - Morningstar Canada, https://global.morningstar.com/en-ca/investments/etfs/0P0000IMT2/portfolio 39. TQQQ: ProShares UltraPro QQQ - ETF Database, https://etfdb.com/etf/TQQQ/ 40. SQQQ: ProShares UltraPro Short QQQ - ETF Database, https://etfdb.com/etf/SQQQ/ 41. Understanding Daily Leveraged ETFs - GraniteShares, https://graniteshares.com/institutional/us/en-us/research/understanding-daily-leveraged-etfs/ 42. Daily Rebalancing & Compounding: Impact on Leveraged ETFs \| LeverageSharesUS, https://leverageshares.com/us/insights/daily-rebalancing-compounding-impact-on-leveraged-etfs/ 43. Leveraged ETFs: A Risky Double That Doesnt Multiply by Two, https://www.financialplanningassociation.org/sites/default/files/2021-08/MAY08%20Leveraged%20ETFs%20A%20Risky%20Double%20That%20Doesnt%20Multiply%20by%20Two.pdf 44. Understanding The Decay Risk in Leveraged ETFs - GraniteShares, https://graniteshares.com/institutional/us/en-us/research/understanding-the-decay-risk-in-leveraged-etfs/ 45. The Mathematics Behind Leveraged ETF Performance: Why Expected Multiples Don't Materialise - ULTUMUS, https://insights.ultumus.com/feed/the-mathematics-behind-leveraged-etf-performance 46. Help me understand the volatility decay of leveraged ETFs : r/quant - Reddit, https://www.reddit.com/r/quant/comments/16gz2em/help\_me\_understand\_the\_volatility\_decay\_of/ 47. Leveraged ETFs: The Hidden Costs of Volatility Drag - Aptus Capital Advisors, https://aptuscapitaladvisors.com/leveraged-etfs-the-hidden-costs-of-volatility-drag/ 48. What Is A Leveraged ETF? Gain or Loss? - Ultima Markets, https://www.ultimamarkets.com/academy/what-is-a-leveraged-etf-gain-or-loss/ 49. Leveraged ETFs Made Easy: How They Work and What to Know - Moomoo, https://www.moomoo.com/us/learn/detail-leveraged-etfs-made-easy-how-they-work-and-what-to-know-117950-250878023 50. Leveraged ETFs: Complete Guide to 2x and 3x ETFs (TQQQ, SQQQ & More) \| Stock Titan, https://www.stocktitan.net/articles/leveraged-etfs-how-they-work 51. QQQ vs TQQQ: Similar Name, Different Game - Nasdaq, https://www.nasdaq.com/articles/qqq-vs-tqqq:-similar-name-different-game-2021-04-07 52. Counterparty and liquidity risks in exchange-traded funds - European Central Bank, https://www.ecb.europa.eu/press/financial-stability-publications/fsr/special/html/ecb.fsrart201811\_3.en.html 53. Frequently Asked Questions about Trading ETFs - ProShares, https://www.proshares.com/faqs/trading-etfs 54. Leveraged and Inverse ETPs: Going, Going, Gone? - Charles Schwab, https://www.schwab.com/learn/story/leveraged-inverse-etfs-going-going-gone 55. ProShares UltraPro Short QQQ ETF: A Guide to SQQQ - Investopedia, https://www.investopedia.com/articles/investing/122215/sqqq-proshares-ultrapro-short-qqq-etf.asp 56. 3 Hedging Strategies To Protect Your Portfolio - Nasdaq, https://www.nasdaq.com/articles/3-hedging-strategies-to-protect-your-portfolio-2020-03-27 57. Short & Leveraged ETPs, https://leverageshares.com/documents/Guide.pdf 58. Hedging With Index-Based ETFs - Investopedia, https://www.investopedia.com/articles/etfs/062716/hedging-etf-indexes-relevant-strategy-qqq-psq.asp 59. SQQQ: Benefits And Risks Of A Leveraged Bear ETF, https://seekingalpha.com/article/4793518-sqqq-benefits-and-risks-of-leveraged-bear-etf 60. The Case for Hedging a Leveraged Long Portfolio with SQQQ to Optimize Risk‑Adjusted Returns - alphaAI Capital, https://www.alphaai.capital/learn/the-case-for-hedging-a-leveraged-long-portfolio-with-sqqq-to-optimize-risk-adjusted-returns 61. inverse and leveraged ETFs: considering the Alternatives - Financial Planning Association, https://www.financialplanningassociation.org/sites/default/files/2021-08/JAN11%20Inverse%20and%20Leveraged%20ETFs%20-%20Considering%20the%20Alternatives.pdf 62. Leveraged and Inverse ETFs - ProShares, https://www.proshares.com/strategies/leveraged-and-inverse 63. Streamline the Short: Strategic Hedging with -1X Inverse ETFs \| Direxion, https://www.direxion.com/education/strategic-hedging-with-inverse-etfs 64. The Lowdown on Leveraged and Inverse Exchange-Traded Products \| FINRA.org, https://www.finra.org/investors/insights/lowdown-leveraged-and-inverse-exchange-traded-products 65. Investor Bulletin: Exchange-Traded Funds (ETFs) - SEC.gov, https://www.sec.gov/investor/alerts/etfs.pdf 66. Economics Note: The Distribution of Leveraged ETF Returns - SEC.gov, https://www.sec.gov/files/dera\_letf\_economics\_note\_nov2019.pdf 67. Leveraged ETFs, Holding Periods and Investment Shortfalls - SLCG Economic Consulting, https://www.slcg.com/files/research-papers/Leveraged%20ETFs,%20Holding%20Periods%20and%20Investment%20Shortfalls.pdf 68. Leveraged ETFs Are Not Worth the Trouble - Timeline, https://www.timeline.co/resources/leveraged-etfs-are-not-worth-the-trouble
