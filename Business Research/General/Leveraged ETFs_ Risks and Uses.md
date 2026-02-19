# Leveraged ETFs: A Comprehensive Analysis of Mechanics, Risks, and Suitability

## Executive Summary

This report provides an expert-level analysis of Leveraged Exchange-Traded Funds (LETFs), specialized financial instruments designed to amplify market returns. A leveraged ETF is an exchange-traded fund engineered to deliver a multiple—such as two times (2x) or three times (3x)—of the *daily* performance of a specific underlying index or asset.

These funds are broadly categorized into three types:

1.  **Leveraged ("Bull") Funds:** These seek positive multiples of an index's daily return. A primary example is the **ProShares UltraPro QQQ (TQQQ)**, which targets 3x the daily performance of the Nasdaq-100 Index.

2.  **Inverse ("Bear") Funds:** These seek to deliver the opposite (-1x) of the daily performance of an index.

3.  **Leveraged Inverse ("Ultra Short") Funds:** These seek a multiple of the opposite (e.g., -2x, -3x) of an index's daily return. The leading example is the **ProShares UltraPro Short QQQ (SQQQ)**, which targets -3x the daily performance of the Nasdaq-100 Index.

The central thesis of this report is that LETFs are sophisticated, high-risk, short-term *trading instruments*, not long-term *investments*. The single most important word in their objective is "daily". This daily objective is not a guideline but a structural mechanism achieved through a "daily reset". This mechanism mathematically guarantees that the fund's performance over any period longer than one day will diverge significantly from the stated multiple. This divergence, known as volatility decay, is the primary source of risk for buy-and-hold investors and the central focus of this analysis.

## 1. The Core Mechanism: Deconstructing the "Daily Reset"

Understanding leveraged ETFs is impossible without first deconstructing the internal mechanics that allow them to provide amplified returns. Their behavior is a direct result of *how* they obtain exposure and *how* they must maintain it.

### 1.1 How LETFs Achieve Exposure: The Role of Derivatives

A traditional exchange-traded fund, such as the Invesco QQQ Trust (QQQ), achieves its objective by purchasing and holding the component stocks of its target index. A leveraged ETF *does not* do this.

To achieve a 3x or -3x exposure, the fund manager must use a portfolio of financial derivatives, primarily **swap agreements** and **futures contracts**.

-   **Swap Agreements:** A swap is a private contract between the fund and a counterparty, typically a major investment bank (e.g., Goldman Sachs, Barclays). For TQQQ, the fund might agree to pay a financing fee to the bank in exchange for receiving 3x the daily return of the Nasdaq-100.

-   **Fund Holdings:** The fund’s assets under management (AUM) are not used to buy stocks, but rather to serve as collateral (often in the form of U.S. Treasury Bills) for these swap contracts.

This derivatives-based structure is how the fund gains a "notional" exposure far larger than its actual asset base.

### 1.2 The Mechanics of Daily Rebalancing

To meet their stated *daily* objective, these funds must "rebalance" or "reset" their exposure at the end of every trading day. This process is mechanical and mandatory, and its consequences dictate the fund's performance path.

-   **Scenario 1: The Index Rises** If the Nasdaq-100 rises 1% on Day 1, TQQQ is designed to rise 3%. The fund's AUM is now higher. To maintain a 3x leverage ratio on this *new, larger* asset base for Day 2, the fund manager is forced to *buy more* derivatives (swaps/futures) to increase its notional exposure.

-   **Scenario 2: The Index Falls** If the Nasdaq-100 falls 1%, TQQQ falls 3%. The fund's AUM is now lower. To avoid becoming *over-leveraged* (e.g., 3.1x) relative to its new, smaller asset base, the fund manager is forced to *sell* derivatives to reduce its exposure.

This non-discretionary rebalancing process creates a forced, pro-cyclical trading strategy. The fund is structurally mandated to "buy high" (increase exposure after a green day) and "sell low" (decrease exposure after a red day). This built-in momentum-chasing behavior is the precise engine of the fund's path-dependent returns. It explains *why* these funds perform exceptionally well in strong, trending markets (where they are rewarded for adding to winning positions) and *why* they are annihilated in volatile, choppy markets (where they are forced to lock in losses on every "whipsaw").

## 2. The Primary Disadvantage: A Quantitative Analysis of Volatility Decay

The "daily reset" mechanism creates the most significant and misunderstood risk associated with LETFs: **volatility decay**.

### 2.1 Defining "Volatility Decay" (or "Variance Drain")

Volatility decay, also known as volatility drag or variance drain, is the mathematical erosion of a LETF's value over time. This decay is not a fee; it is an inescapable mathematical property of compounding volatile, leveraged returns.

The effect of this decay is most pronounced in volatile, sideways, or "choppy" markets. In such conditions, the daily rebalancing causes the LETF to lose value *even if the underlying index finishes the period flat or slightly positive*.

### 2.2 A Mathematical Example of Decay

This "path dependency" is best illustrated with a simple two-day example, modeled on principles from financial analysis.

**Assumptions:**

-   **Investor A** holds $100 of a 1x Index ETF (tracking the Nasdaq-100, like QQQ).

-   **Investor B** holds $100 of a 3x Bull ETF (TQQQ).

-   **Investor C** holds $100 of a -3x Bear ETF (SQQQ).

**Day 1: A Volatile Up Day.** The Index rises **+10%**.

-   Investor A (1x): $100.00 \\times 1.10 = **$110.00**

-   Investor B (3x): $100.00 \\times 1.30 = **$130.00** (Fund rebalances by *buying more* exposure)

-   Investor C (-3x): $100.00 \\times 0.70 = **$70.00** (Fund rebalances by *reducing* short exposure)

**Day 2: A Volatile Down Day.** The Index falls **-9.09%**.

-   *Result for Index:* The index falls from 110.00 by 9.09% (110 \\times 0.0909 = 10). It lands at $100.00.

-   *Overall Index Return:* The index is **perfectly flat** (100 \\rightarrow 100 = 0\\% return).

**Day 2: Calculating the LETF Returns...**

-   **Investor A (1x):** $110.00 \\times (1 - 0.0909) = **$100.00**

    -   **Net Return: 0.00%**

-   **Investor B (3x):** The ETF must deliver 3 \\times -9.09% = **-27.27%**. This is calculated from its *new* 130.00 value.

    -   $130.00 \\times (1 - 0.2727) = **$94.55**

    -   **Net Return: -5.45%**

-   **Investor C (-3x):** The ETF must deliver -3 \\times -9.09% = **+27.27%**. This is calculated from its *new* 70.00 value.

    -   $70.00 \\times (1 + 0.2727) = **$89.09**

    -   **Net Return: -10.91%**

### 2.3 Table 1: The Mathematics of Volatility Decay (Hypothetical 2-Day Example)

The results from this hypothetical scenario are summarized below.

| Instrument          | Start Value | Day 1 (Index +10%) | Day 2 (Index -9.09%) | End Value | Net Return  |
|---------------------|-------------|--------------------|----------------------|-----------|-------------|
| 1x Index ETF (QQQ)  | $100.00     | $110.00            | $100.00              | $100.00   | **0.00%**   |
| 3x Bull ETF (TQQQ)  | $100.00     | $130.00            | $94.55               | $94.55    | **-5.45%**  |
| -3x Bear ETF (SQQQ) | $100.00     | $70.00             | $89.09               | $89.09    | **-10.91%** |

This example reveals a critical truth: in a volatile, "whipsaw" market that ends flat, *both the bull (TQQQ) and bear (SQQQ) funds lose significant value*. This decay is not a directional problem; it is a *volatility* problem. The common retail strategy of holding both TQQQ and SQQQ as a "hedge" is not a hedge at all; in a choppy market, it is a "lose-lose" scenario.

### 2.4 The Compounding "Boost": The Other Side of the Coin

The daily reset mechanism is not *always* a disadvantage. In a *strong, low-volatility, trending market*, the compounding effect works in the LETF's favor, creating a "compounding boost".

Consider a 2-day *uptrend* :

-   **Day 1:** Index +10% (Value: 110) \| 2x ETF +20% (Value: 120)

-   **Day 2:** Index +10% (Value: 121) \| 2x ETF +20% (calculated from the new 120 base) = +24 (Value: 144)

In this scenario, the index gained 21% over two days. The 2x ETF gained 44%—*more than* 2x the index's total return. This directly answers the question of the "best situation" for these funds: a high-momentum, low-volatility, trending market where the "buy high" mechanism is consistently rewarded.

## 3. A Balanced Analysis: Advantages and Severe Risks

Weighing the potential benefits against the structural flaws is essential.

### 3.1 Advantages

1.  **Magnified Short-Term Gains:** This is the primary allure. A correct 1-day (or very short-term) call on market direction can be amplified by 2x or 3x, offering the potential for significant returns in a short period.

2.  **Capital Efficiency:** LETFs allow a trader to gain a large notional exposure with a relatively small amount of capital. For example, a 10,000 position in TQQQ provides 30,000 of exposure to the Nasdaq-100.

3.  **Accessibility and Convenience:** The funds provide leveraged or short exposure through a simple ETF ticker that can be traded in any standard brokerage account. This allows traders to bypass the complexities and account requirements of using margin, futures contracts, or options.

4.  **Ability to Profit from Downturns:** Inverse and leveraged inverse ETFs (like SQQQ) offer a straightforward way to speculate on or hedge against market declines.

### 3.2 Disadvantages and Severe Risks

1.  **Magnified, Potentially Catastrophic Losses:** Leverage is a double-edged sword. A 10% index drop in one day will cause an immediate \~30% loss in a 3x fund. A 33.4% index drop would *theoretically* wipe out the fund's entire value in a single session. Drawdowns are severe and happen rapidly.

2.  **Volatility Decay:** As detailed in Section 2, this constant erosion of value makes the funds *fundamentally* unsuitable for their most common misuse: long-term, buy-and-hold investing.

3.  **High Expense Ratios:** LETFs are far more expensive than traditional ETFs. While a standard index ETF like QQQ has an expense ratio of \~0.20% , leveraged ETFs charge fees approaching 1.00% or more.

    -   **TQQQ Expense Ratio:** 0.82% to 0.97%.

    -   **SQQQ Expense Ratio:** 0.95%. This high fee is an *additional* drag on performance, separate from volatility decay.

4.  **Tax Inefficiency:** The fund's constant daily rebalancing of its derivative portfolio can generate a high volume of short-term capital gains, which are often passed on to investors and taxed at higher ordinary income rates.

5.  **Counterparty Risk:** This is a hidden, systemic risk. An investor in QQQ owns a fractional share of underlying stocks. An investor in TQQQ or SQQQ *does not*. They own a fund whose primary assets are *promises* (swap agreements) from investment banks. The holdings of SQQQ, for example, show massive swap positions with counterparties like Goldman Sachs and Barclays. If a major counterparty were to fail in a systemic crisis, the ETF could be unable to meet its objective or could suffer a catastrophic loss, *even if the underlying index was performing as expected*.

## 4. Case Study: The Nasdaq-100 Bull (ProShares UltraPro QQQ - TQQQ)

Analyzing the most popular leveraged ETF, TQQQ, provides a clear picture of these forces in action.

-   **Fund Objective:** To seek daily investment results, before fees and expenses, that correspond to **three times (3x) the daily performance** of the Nasdaq-100 Index.

-   **Fund Profile:**

    -   **Issuer:** ProShares

    -   **Inception Date:** February 9, 2010

    -   **Expense Ratio:** \~0.82% - 0.97%

    -   **Mechanism:** Uses futures and swap agreements to achieve its 3x daily target.

### 4.1 Performance Analysis (Regime 1: Bull Market)

TQQQ's 2010 launch was, by pure chance, at the beginning of one of the strongest, longest-running, and lowest-volatility bull markets in technology history. This was the *absolute perfect* environment for the fund. The "compounding boost" effect (Section 2.4) worked brilliantly.

-   **Result:** TQQQ generated staggering, life-changing returns. As of mid-2025, 10-year data showed the underlying QQQ return at +453%, while TQQQ's return was **+1,830%**. Other data sets show a 10-year return of **+4,395%** versus QQQ's +447%. This performance, driven by positive compounding, is what allures new traders.

### 4.2 Performance Analysis (Regime 2: Bear Market)

The 2022 bear market demonstrated the catastrophic risk.

-   **Result:** While the underlying QQQ index lost **32.58%** in 2022 , TQQQ experienced a maximum drawdown of **-81.65%**.

-   This illustrates the "constant leverage trap". An 81.65% loss requires a **+444% gain** just to break even. This deep loss "de-couples" the fund from its long-term index. One analysis highlighted a recovery period where the QQQ index was *up 1.31%*, but TQQQ was still **down -41.64%** from the same starting date.

-   **Conclusion:** A single bear market can wipe out *years* of compounded gains and create a performance gap so large that the fund may *never* recover its previous high, even as the underlying index does.

## 5. Case Study: The Nasdaq-100 Bear (ProShares UltraPro Short QQQ - SQQQ)

Analyzing the most popular inverse ETF, SQQQ, reveals the other side of the decay problem.

-   **Fund Objective:** To seek daily investment results, before fees and expenses, that correspond to **three times the inverse (-3x) the daily performance** of the Nasdaq-100 Index.

-   **Fund Profile:**

    -   **Issuer:** ProShares

    -   **Inception Date:** February 9, 2010

    -   **Expense Ratio:** \~0.95%

    -   **Mechanism:** Uses cash/T-bill collateral to back a large portfolio of swap agreements that are short the Nasdaq-100.

### 5.1 Performance Analysis (Regime 1: Bear Market)

During a sharp downturn, SQQQ performs its job *for a short-term trader*. If the Nasdaq-100 falls 2% in a day, SQQQ aims to rise 6%. Traders who correctly time a bear market (like in 2022 or 2018) can use SQQQ for rapid gains.

### 5.2 Performance Analysis (Regime 2: Long-Term Holding)

Holding SQQQ as a long-term "investment" or hedge is a *guaranteed* path to near-total loss.

-   **Result:** The 10-year annualized return for SQQQ is approximately **-54.7%**. Its 5-year total return is approximately **-97.37%**.

SQQQ's value is relentlessly destroyed by two powerful forces:

1.  **Positive Market Drift:** The stock market, and particularly the growth-oriented Nasdaq-100, has a strong positive bias over long periods. A fund structurally designed to be -3x short is fighting this powerful, permanent uptrend.

2.  **Volatility Decay:** As demonstrated in Table 1, volatility decay erodes the value of *both* bull and bear funds. A choppy market (up 1%, down 1%) is a "lose-lose" scenario.

Because of these two factors, SQQQ is a *depreciating asset* by design. It is built for *timing* a downturn, not for "investing" in one.

### 5.3 Table 2: Fund Profile & Risk Comparison

| Feature                       | QQQ (Invesco QQQ Trust) | TQQQ (ProShares UltraPro QQQ)      | SQQQ (ProShares UltraPro Short QQQ)     |
|-------------------------------|-------------------------|------------------------------------|-----------------------------------------|
| **Stated Objective**          | Tracks Nasdaq-100 Index | **3x DAILY** return of Nasdaq-100  | **-3x DAILY** return of Nasdaq-100      |
| **Leverage**                  | 1x (None)               | 3x (Bull)                          | -3x (Bear / Inverse)                    |
| **Mechanism**                 | Holds component stocks  | Derivatives (Swaps, Futures)       | Derivatives (Swaps, Futures)            |
| **Expense Ratio**             | \~0.20%                 | \~0.82% - 0.97%                    | \~0.95%                                 |
| **10-Yr Return (Annualized)** | \~+19%                  | \~+35% (Highly path-dependent)     | \~-54.7%                                |
| **Max Drawdown (5-Yr)**       | \~-33% (2022)           | \~-81.65%                          | \~-97.37% (5-Yr loss)                   |
| **Primary Risk**              | Market Risk             | Volatility Decay, Magnified Losses | Volatility Decay, Positive Market Drift |

## 6. The Hedging Conundrum: A Tactical Tool, Not a Strategic Shield

This analysis leads directly to the user's question: "Can it be used for hedging?"

The simple answer is yes; inverse ETFs are *marketed* for this exact purpose. An investor with a large 300,000 portfolio of QQQ who fears a short-term correction could, in theory, buy 100,000 of SQQQ to neutralize their exposure. This is more capital-efficient than shorting 300,000 worth of stock or buying 300,000 of a -1x fund.

However, this is a *tactical* hedge for *days*, not a *strategic* hedge for weeks or months.

The "hedge" itself is a depreciating asset that *decays* (see Section 5.2). If an investor holds an SQQQ hedge for months, they will likely lose money on the hedge *even if the market moves in their favor* due to volatility drag. In a nightmare scenario, the decay can be so severe that the inverse ETF *loses money* at the same time the asset it's hedging *also loses money*. One study of a different leveraged inverse ETF found it *declined 21%* during a period when its underlying index *also fell*. The hedge not only failed but *compounded the investor's losses*.

A true hedge, like a put option or a long-term bond, is designed to provide "peace of mind." A leveraged ETF, which requires *daily monitoring* per its own prospectus and regulatory warnings , fails this test. It is not a passive, strategic shield. It is an *active, short-term, speculative trade* that runs opposite to a main position.

## 7. Conclusion: The Ideal Situation and Investor Profile

This report concludes with a direct answer to the user's final question: "In which situation is best for investing in them?"

### 7.1 The "Investment" Misconception

The single most important conclusion of this analysis is that the "best situation" for "investing" in a leveraged ETF *does not exist*.

The word "investing" implies a buy-and-hold strategy. The overwhelming evidence from quantitative analysis and regulatory bodies (SEC, FINRA) proves this is the *worst* possible use for these products. The SEC and FINRA have issued numerous investor alerts stating these funds are unsuitable for retail investors who plan to hold them for longer than **one trading session**.

### 7.2 The Optimal "Trading" Scenario

The correct term for their use is "trading." The ideal scenario for *trading* a leveraged ETF like TQQQ or SQQQ requires three specific conditions:

1.  **A High-Conviction, Short-Term Directional Call:** The trader must have a strong thesis on the market's direction for *that day* or the next few days.

2.  **A Strong, Trending Market (High Momentum):** The products perform best when the market is moving decisively in one direction. This allows the daily reset to compound *positively* (Section 2.4).

3.  **A Low-Volatility Regime:** The ideal move is a "strong, smooth trend," not a "choppy" or "volatile" one. High volatility, even if in the correct direction, will erode returns via decay.

### 7.3 The Profile of the Suitable "Trader"

Given the extreme risks and complex mechanics, the *only* suitable user for these products is *not* a typical investor. The suitable profile is a trader who is:

1.  **Sophisticated:** They must fully and quantitatively understand the mechanics of daily rebalancing, compounding, volatility decay, and counterparty risk.

2.  **Highly Active & Disciplined:** They must have a "Most Aggressive" investment objective and possess the discipline and ability to *actively monitor their positions daily*, if not hourly.

3.  **Short-Term:** They must be using the product for its intended purpose: intraday speculation or as a *tactical* hedge lasting only a few days.

In summary, leveraged ETFs are akin to "Formula 1 cars in a world of family sedans". They are alluring due to their potential for spectacular returns , but they are high-fee , structurally complex , and carry risks that can lead to rapid, significant, and potentially total losses. They are, by their very design, unsuitable for the vast majority of all investors.

#### Works cited

1\. Updated Investor Bulletin: Leveraged and Inverse ETFs, https://www.investor.gov/introduction-investing/general-resources/news-alerts/alerts-bulletins/investor-alerts/sec 2. TQQQ: The World's Largest Leveraged ETF - ProShares, https://www.proshares.com/browse-all-insights/insights/tqqq-the-worlds-largest-leveraged-etf 3. Non-Traditional ETFs FAQ \| FINRA.org, https://www.finra.org/rules-guidance/key-topics/etf/non-traditional-etf-faq 4. SQQQ \| UltraPro Short QQQ - ProShares, https://www.proshares.com/our-etfs/leveraged-and-inverse/sqqq 5. Frequently Asked Questions on Performance and Pricing - ProShares, https://www.proshares.com/faqs/performance-pricing-faqs 6. Understanding Daily Leveraged ETFs - GraniteShares, https://graniteshares.com/institutional/us/en-us/research/understanding-daily-leveraged-etfs/ 7. Leveraged ETFs - Fidelity Investments, https://www.fidelity.com/learning-center/investment-products/etf/types-of-etfs-leveraged-etfs 8. Leveraged ETFs: A Risky Double That Doesnt Multiply by Two, https://www.financialplanningassociation.org/sites/default/files/2021-08/MAY08%20Leveraged%20ETFs%20A%20Risky%20Double%20That%20Doesnt%20Multiply%20by%20Two.pdf 9. TQQQ vs. QQQ: What's the Difference? - Investopedia, https://www.investopedia.com/investing/qqq-vs-tqqq-difference-and-which-better/ 10. TQQQ Profile - ETF Guide - SumGrowth, https://www.sumgrowth.com/etf-profile/invest-in-TQQQ-etf.html 11. Leveraged ETFs Explained: How They Work, Risks, and Benefits \| LeverageSharesUS, https://leverageshares.com/us/insights/leveraged-etfs-explained-how-they-work-risks-and-benefits/ 12. Understanding Leveraged & Inverse Exchange Traded Funds - Direxion, https://www.direxion.com/education/understanding-leveraged-exchange-traded-funds 13. Compounding Effects in Leveraged ETFs: Beyond the Volatility Drag ParadigmThis manuscript is a preprint and is currently under review for publication. - arXiv, https://arxiv.org/html/2504.20116v1 14. ProShares UltraPro Short QQQ SQQQ ETF Portfolio Review - Morningstar Canada, https://global.morningstar.com/en-ca/investments/etfs/0P0000IMT2/portfolio 15. Thinking About a Short or Inverse ETF? Read This First - Nasdaq, https://www.nasdaq.com/articles/thinking-about-a-short-or-inverse-etf-read-this-first 16. TQQQ: Read This First Before Leveraging The Nasdaq-100 For 3x Potential Returns, https://seekingalpha.com/article/4787742-tqqq-read-this-first-before-leveraging-the-nasdaq-100-for-3x-potential-returns 17. TQQQ: ProShares UltraPro QQQ - ETF Database, https://etfdb.com/etf/TQQQ/ 18. SQQQ: ProShares UltraPro Short QQQ - ETF Database, https://etfdb.com/etf/SQQQ/ 19. Why Do Leveraged ETFs Decay? Understanding the Mechanics and Risks, https://www.crystalfunds.com/insights/leveraged-etfs-decay-understanding-mechanics-and-risks 20. Daily Rebalancing & Compounding: Impact on Leveraged ETFs \| LeverageSharesUS, https://leverageshares.com/us/insights/daily-rebalancing-compounding-impact-on-leveraged-etfs/ 21. Leveraged ETFs: Amplifying Gains or Risks? - ArchBridge Family Office, https://archbridge.com/insights/leveraged-etfs-amplifying-gains-or-risks/ 22. What Is A Leveraged ETF? Gain or Loss? - Ultima Markets, https://www.ultimamarkets.com/academy/what-is-a-leveraged-etf-gain-or-loss/ 23. Understanding The Decay Risk in Leveraged ETFs - GraniteShares, https://graniteshares.com/institutional/us/en-us/research/understanding-the-decay-risk-in-leveraged-etfs/ 24. The Mathematics Behind Leveraged ETF Performance: Why Expected Multiples Don't Materialise - ULTUMUS, https://insights.ultumus.com/feed/the-mathematics-behind-leveraged-etf-performance 25. Help me understand the volatility decay of leveraged ETFs : r/quant - Reddit, https://www.reddit.com/r/quant/comments/16gz2em/help\_me\_understand\_the\_volatility\_decay\_of/ 26. Leveraged ETFs Made Easy: How They Work and What to Know - Moomoo, https://www.moomoo.com/us/learn/detail-leveraged-etfs-made-easy-how-they-work-and-what-to-know-117950-250878023 27. The “Rebalance Drag” Myth in Leveraged ETFs: What Advisors Need to Know, https://www.returnstacked.com/the-rebalance-drag-myth-in-leveraged-etfs-what-advisors-need-to-know/ 28. Leveraged ETFs: The Hidden Costs of Volatility Drag - Aptus Capital Advisors, https://aptuscapitaladvisors.com/leveraged-etfs-the-hidden-costs-of-volatility-drag/ 29. Can a person invest in SQQQ and TQQQ, using trailing stop losses, to come out ahead in the market? : r/stocks - Reddit, https://www.reddit.com/r/stocks/comments/16hyu5a/can\_a\_person\_invest\_in\_sqqq\_and\_tqqq\_using/ 30. What are Leveraged ETFs and how do they work? - IG Group, https://www.ig.com/en/trading-strategies/leveraged-etfs--what-are-they-and-how-do-they-work--230605 31. 7 Best Leveraged ETFs for November 2025 - NerdWallet, https://www.nerdwallet.com/article/investing/leveraged-etf 32. The Pricing Efficiency of Leveraged Exchange-Traded Funds, https://www.efmaefm.org/0efmameetings/efma%20annual%20meetings/2012-Barcelona/papers/EFMA2012\_0524\_fullpaper.pdf 33. TQQQ \| UltraPro QQQ - ProShares, https://www.proshares.com/our-etfs/leveraged-and-inverse/tqqq 34. Daily Reset, Long-Term Risk: Why Leveraged ETFs Aren't Built for Buy-and-Hold - Minnesota Valley Grain -, https://www.mnvalleygrain.com/news/story/35838311/daily-reset-long-term-risk-why-leveraged-etfs-aren-t-built-for-buy-and-hold 35. What Are Inverse ETFs? - INDmoney, https://www.indmoney.com/blog/us-stocks/what-are-inverse-etfs 36. How Inverse ETFs Protect and Enhance Your Portfolio - Investopedia, https://www.investopedia.com/articles/mutualfund/07/inverse-etfs.asp 37. What are Leveraged Funds - Advantages & Disadvantages - Scripbox, https://scripbox.com/mf/leveraged-etf/ 38. QQQ vs TQQQ: Similar Name, Different Game - Nasdaq, https://www.nasdaq.com/articles/qqq-vs-tqqq:-similar-name-different-game-2021-04-07 39. investing in QQQ vs TQQQ for the longterm - Reddit, https://www.reddit.com/r/investing/comments/18n4fqh/investing\_in\_qqq\_vs\_tqqq\_for\_the\_longterm/ 40. Risks of Complex Registered Funds \| JP Morgan, https://www.jpmorgan.com/content/dam/jpm/securities/documents/investing-in-non-traditional-funds.pdf 41. QQQ vs SQQQ \| ETF Performance Comparison Tool - Composer.trade, https://www.composer.trade/etf-comparisons/QQQ-SQQQ 42. Leveraged Equities ETFs - ETF Database, https://etfdb.com/etfdb-category/leveraged-equities/ 43. SUMMARY PROSPECTUS - UltraPro QQQ - ProShares, https://www.proshares.com/globalassets/proshares/prospectuses/tqqq\_summary\_prospectus.pdf 44. TQQQ Offers Broader Tech Exposure Than SOXL - Nasdaq, https://www.nasdaq.com/articles/tqqq-offers-broader-tech-exposure-soxl 45. ProShares UltraPro QQQ: TQQQ Stock Price Quote & News - Robinhood, https://robinhood.com/us/en/stocks/TQQQ/ 46. SQQQ ETF Profile ProShares Ultrapro Short QQQ - Market Chameleon, https://marketchameleon.com/Overview/SQQQ/ETFProfile/ 47. Inverse, Leveraged and Volatility ETFs: What's the Difference? - Chase.com, https://www.chase.com/personal/investments/learning-and-insights/article/inversed-vs-leveraged-vs-volatile-etfs 48. The Lowdown on Leveraged and Inverse Exchange-Traded Products \| FINRA.org, https://www.finra.org/investors/insights/lowdown-leveraged-and-inverse-exchange-traded-products 49. Counterparty and liquidity risks in exchange-traded funds - European Central Bank, https://www.ecb.europa.eu/press/financial-stability-publications/fsr/special/html/ecb.fsrart201811\_3.en.html 50. ProShares UltraPro QQQ, https://www.schwab.wallst.com/schwab/Prospect/research/etfs/reports/reportRetrieve.asp?reportType=etfrc&symbol=TQQQ 51. 2 Reasons to Buy TQQQ, and 3 Reasons Not To - Nasdaq, https://www.nasdaq.com/articles/2-reasons-buy-tqqq-and-3-reasons-not 52. Compare QQQ vs TQQQ to Make an Informed Choice - Pearler, https://pearler.com/explore/invest/us-shares/compare/QQQ-vs-TQQQ/performance 53. The Reality of Trading TQQQ and Key Strategies - YouTube, https://www.youtube.com/watch?v=4-IjRmw7SZI 54. Understanding QQQ's performance through market cycles \| Invesco US, https://www.invesco.com/qqq-etf/en/innovation/understanding-qqqs-performance-through-market-cycles.html 55. Why is it bad to hold leveraged ETFs?, https://www.reddit.com/r/ETFs/comments/1nk4o83/why\_is\_it\_bad\_to\_hold\_leveraged\_etfs/ 56. proshares ultrapro short qqq - SEC.gov, https://www.sec.gov/Archives/edgar/data/1174610/000119312518287997/d620881d497k.htm 57. Why Bitcoin's Correlation with Equities Makes SQQQ a Smart Hedge - alphaAI Capital, https://www.alphaai.capital/learn/why-bitcoins-correlation-with-equities-makes-sqqq-a-smart-hedge 58. Top 3 Inverse Index ETFs to Short the Market in 2023 - Investopedia, https://www.investopedia.com/inverse-index-etfs-bear-with-them-in-january-4582506 59. SQQQ: Benefits And Risks Of A Leveraged Bear ETF, https://seekingalpha.com/article/4793518-sqqq-benefits-and-risks-of-leveraged-bear-etf 60. So what's the downside of holding SQQQ for a years, seems way more likely to double than the SP500 or dow to do a 2x : r/investing - Reddit, https://www.reddit.com/r/investing/comments/1ddjmti/so\_whats\_the\_downside\_of\_holding\_sqqq\_for\_a\_years/ 61. ProShares UltraPro Short QQQ, https://www.schwab.wallst.com/schwab/Prospect/research/etfs/reports/reportRetrieve.asp?reportType=etfrc&symbol=SQQQ 62. SQQQ ProShares UltraPro Short QQQ - ETF Guide - SumGrowth, https://www.sumgrowth.com/etf-profile/invest-in-SQQQ-etf.html 63. Help understand the whole proshare qqq world : r/investing - Reddit, https://www.reddit.com/r/investing/comments/1dux33c/help\_understand\_the\_whole\_proshare\_qqq\_world/ 64. ProShares UltraPro Short QQQ ETF: A Guide to SQQQ - Investopedia, https://www.investopedia.com/articles/investing/122215/sqqq-proshares-ultrapro-short-qqq-etf.asp 65. Hedging With Index-Based ETFs - Investopedia, https://www.investopedia.com/articles/etfs/062716/hedging-etf-indexes-relevant-strategy-qqq-psq.asp 66. 3 Hedging Strategies To Protect Your Portfolio - Nasdaq, https://www.nasdaq.com/articles/3-hedging-strategies-to-protect-your-portfolio-2020-03-27 67. The Pitfalls of Leveraged and Inverse ETFs - CFA Institute Research and Policy Center, https://rpc.cfainstitute.org/research/cfa-magazine/2009/the-pitfalls-of-leveraged-and-inverse-etfs 68. Frequently Asked Questions about Trading ETFs - ProShares, https://www.proshares.com/faqs/trading-etfs 69. The Case for Hedging a Leveraged Long Portfolio with SQQQ to Optimize Risk‑Adjusted Returns - alphaAI Capital, https://www.alphaai.capital/learn/the-case-for-hedging-a-leveraged-long-portfolio-with-sqqq-to-optimize-risk-adjusted-returns 70. Adviser Alert: Inverse and Leveraged ETFs \| DORA - Colorado Division of Securities, https://securities.colorado.gov/press-release/adviser-alert-inverse-and-leveraged-etfs 71. Regulatory Notice 09-31 \| FINRA.org, https://www.finra.org/rules-guidance/notices/09-31 72. Investor Bulletin: Exchange-Traded Funds (ETFs) - SEC.gov, https://www.sec.gov/investor/alerts/etfs.pdf 73. Leveraged ETFs: Complete Guide to 2x and 3x ETFs (TQQQ, SQQQ & More) \| Stock Titan, https://www.stocktitan.net/articles/leveraged-etfs-how-they-work 74. Leveraged ETFs, Holding Periods and Investment Shortfalls - SLCG Economic Consulting, https://www.slcg.com/files/research-papers/Leveraged%20ETFs,%20Holding%20Periods%20and%20Investment%20Shortfalls.pdf 75. Leveraged ETFs Are Not Worth the Trouble - Timeline, https://www.timeline.co/resources/leveraged-etfs-are-not-worth-the-trouble
