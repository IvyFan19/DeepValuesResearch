---
title: "Deconstructing Index Mechanics and Real Returns: A Value Investor’s Comparative Analysis of US and Chinese Equity Markets"
date: "2026-11-02"
lang: "en"
category: "investing"
tickers: []
notebook_id: "86107a89-32b7-4c7e-8957-17fdf0e2345a"
source_urls:
  - title: "【李永乐老师】中美股市哪个更赚钱？为什么道指屡创新高，上证指数永远3000点？"
    url: "https://www.youtube.com/watch?v=JKljQMMaBxE"
youtube:
  - title: "Shanghai vs Dow: How a Flat 3,000 Hid 9% Real Annual Returns"
    url: "https://youtu.be/XW8SVllB9Bk"
    lang: "en"
    publish_at: "2026-11-05T22:00:00Z"
  - title: "道瓊破5萬、上證卡三千：年化9%為何散戶仍虧錢？"
    url: "https://youtu.be/j2jKwXQOJKQ"
    lang: "zh"
    publish_at: "2026-11-06T12:00:00Z"
podcast:
  - title: "Shanghai vs Dow: How a Flat 3,000 Hid 9% Real Annual Returns | Stock Market"
    url: "https://open.spotify.com/episode/5W4VGmqOVWtYQ4siXNuYu0"
    lang: "en"
  - title: "道瓊破5萬、上證卡三千：年化9%為何散戶仍虧錢？｜美股市場"
    url: "https://open.spotify.com/episode/1PtRYIuA6VNDHBPNx9LWIw"
    lang: "zh"
generated_by: "NotebookLM + DeepValues editors"
disclosure: "AI-assisted"
---

# Deconstructing Index Mechanics and Real Returns: A Value Investor’s Comparative Analysis of US and Chinese Equity Markets

Investors frequently ask why headline equity indices display such stark visual divergence—specifically, why the Shanghai Stock Exchange Composite Index appears persistently anchored around the 3,000-point mark while the Dow Jones Industrial Average regularly reaches record highs, and whether US equities truly outperform Chinese equities over multi-decade horizons. The resolution to this paradox lies in index construction methodology: price-weighted, float-adjusted, and total market-capitalization frameworks introduce structural distortions into headline index figures. However, when evaluated through a value-investing framework that incorporates reinvested cash dividends and adjusts for purchasing-power inflation, both markets have delivered strong real compound returns (6.6% annual real return for US equities vs. 9.0% annual real return for the Shanghai Composite since 1990). Ultimately, long-term wealth generation is governed by underlying corporate owner earnings, capital allocation mechanisms—such as share buybacks versus float dilution—and investor behavior, rather than flawed headline index numbers.

---

## 1. The Evolution and Mechanics of Stock Market Indices: DJIA vs. S&P 500

Understanding modern equity benchmark indicators requires examining the historical evolution of US financial market infrastructure. Unregulated equity trading in the United States began in 1790 following the establishment of the Philadelphia Stock Exchange. To curb market manipulation, counterparty failures, and frequent trading scandals, 24 prominent stockbrokers gathered under a buttonwood tree on Wall Street in New York City in 1792 to sign the landmark Buttonwood Agreement. This document instituted formal market governance by setting strict broker qualification standards and mandating a minimum commission rate of 0.25% on all transactions. Over subsequent decades, this broker network expanded, culminating in the formal founding of the New York Stock Exchange (NYSE) in 1863.

In the late 19th century, investors lacked an efficient quantitative tool to track broad equity price movements beyond manually reviewing physical exchange blackboards or requesting quotes from trading clerks. To eliminate this opacity, Charles Dow—who had not completed middle school but possessed sharp market intuition—and Edward Jones founded the Dow Jones Company. Initially delivering daily price updates to financial subscribers via telephone, they developed a consolidated quantitative summary of market performance: the Dow Jones Industrial Average (DJIA), first published on May 26, 1896, with a baseline value of 40.94 points. Printed daily in their newly established financial newspaper, *The Wall Street Journal*, the index initially tracked 12 prominent industrial enterprises driving American economic expansion, including cotton producers, tobacco syndicates, and General Electric.

Despite its historic status, the DJIA relies on a price-weighted calculation methodology that introduces inherent structural distortions:

$$\text{DJIA} = \frac{\sum_{i=1}^{N} P_i}{D}$$

where $P_i$ represents the absolute share price of constituent stock $i$, and $D$ represents the index divisor. Under price-weighting, a firm trading at a high absolute dollar price per share exerts a disproportionately larger influence on index movements than a lower-priced firm, regardless of total corporate capitalization, net assets, outstanding shares, or macroeconomic scale. 

To expand market coverage, the DJIA increased its constituent base from 12 to 30 enterprises in 1928, resetting its baseline index value to 100 points on October 1, 1928. Membership within the index is periodically adjusted: stagnant or declining industrial enterprises are removed and replaced by growing businesses. In 2018, General Electric—the final remaining member of the original 1896 constituent group—was formally removed from the index.

To address the distortions inherent in price-weighting, Standard & Poor's introduced the S&P 500 index in 1957. The S&P 500 utilizes a float-adjusted market-capitalization weighting framework:

$$\text{S&P 500 Index} = \frac{\sum_{i=1}^{N} (P_i \times Q_i)}{\text{Divisor}}$$

where $P_i$ represents the current market price of constituent $i$, and $Q_i$ represents the tradeable float (the publicly available share quantity excluding locked insider or state holdings). By weighting constituents according to tradeable float market capitalization, the S&P 500 reflects accessible market liquidity. Furthermore, the mathematical divisor is dynamically adjusted whenever constituent stocks are replaced, corporate rights issues occur, or structural capital changes take place. This continuous divisor modification preserves index continuity, ensuring that daily point shifts reflect pure underlying asset price movements rather than artificial capital additions or subtractions.

---

## 2. Historical Real Returns: Factoring Dividends and Inflation

Evaluating multi-decade market performance exclusively through headline index levels introduces fundamental errors by ignoring cash dividend distributions and purchasing-power inflation.

Over a 98-year evaluation window from October 1, 1928 (when the DJIA baseline was set at 100 points) to October 1, 2026 (with the index reaching 52,867.98 points), the DJIA generated a nominal compound annual growth rate (CAGR) of 6.6%:

$$100 \times (1 + R)^{98} = 52,867.98 \implies R \approx 6.6\%$$

Applying the Rule of 72, a nominal annual return of 6.6% doubles invested capital approximately every 11 years, significantly outpacing basic banking deposits and sovereign debt yields over the same horizon.

A multi-decade performance breakdown of the S&P 500 from 1957 to 2026 further illustrates the critical mathematical impact of dividend reinvestment and inflation adjustments:

* **Nominal Index Price Return:** The price-only S&P 500 index delivered an average nominal return of 7.7% per annum.
* **Total Return (Dividend Reinvestment):** Reinvesting all cash dividend distributions back into constituent equities raised the nominal compound return to 10.5% per annum.
* **Real Net Return (Inflation-Adjusted):** Subtracting monetary inflation from total compound returns yields a real compound return of 6.6% per annum.

From a Graham-Buffett value-investing perspective, price-only index charts fail Benjamin Graham's fundamental "Owner Earnings" test. When a corporation distributes a cash dividend, its share price drops by the ex-dividend amount on the exchange. Price-only indices register this price reduction strictly as a capital loss, treating cash distributions as value destruction rather than a direct transfer of liquid capital from the corporate treasury to the investor's balance sheet. Over multi-decade holding periods, retained earnings reinvestment combined with cumulative cash dividends constitutes a core engine of total owner return. Omitting cash distributions severely understates the true compounding power of equity ownership.

---

## 3. Origins and Structural Distortions of the Shanghai Composite Index

China's experience with corporate equity infrastructure spans over a century and a half. In 1872, Westernization Movement leaders Li Hongzhang and Sheng Xuanhuai established the China Merchants Steam Navigation Company, issuing China's first public business shares. (This historical origin is commemorated on the Shanghai Stock Exchange by assigning ticker code 601872 to China Merchants Steamship). Institutional equity trading expanded with the establishment of the Shanghai Shares Guild in 1891 and the formal founding of the Shanghai Stock Exchange in 1904. Following the creation of the People's Republic of China in 1949, capitalist financial exchanges were closed.

Equity securities resurfaced during the Reform and Opening-Up period. In 1984, the nationwide popularity of Taiwanese singer Deng Lijun (Teresa Teng) swept across mainland China. Because standard television set and radio speakers could not deliver the audio fidelity desired by listeners, consumer demand for high-quality audio speaker systems expanded rapidly. Capitalizing on this market dynamic, Qin Bin, manager of the Shanghai Electrical General Factory, sought to build an advanced speaker production line. Lacking capital for factory expansion, Qin proposed raising funds by issuing stock certificates directly to plant workers. 

However, a media report by the *Xinmin Evening News* inadvertently stated that shares were being offered to the general public. Enthusiastic citizens flooded the newspaper's offices with inquiries regarding purchasing logistics. To resolve the public clamor, media executives persuaded Qin to allocate a portion of the issue to the public. On November 18, 1984, Shanghai Feilo Acoustics launched New China's first public equity offering, selling out its 500,000 public shares almost instantly as crowds thronged the factory gates.

To facilitate secondary market trading, the Shanghai Trust Jing'an Sales Department opened on September 26, 1986. That same year, NYSE Chairman John Phelan visited Beijing and presented Deng Xiaoping with an exchange VIP pass. In return, Deng presented Phelan with a physical stock certificate of Feilo Acoustics. Seeking to verify the operational authenticity of Chinese equity ownership, Phelan traveled directly to the Jing'an Sales Department in Shanghai to process the stock transfer manually into his name. Following these pilot initiatives, Deng Xiaoping articulated a clear policy directive: capital markets are not unique to capitalism; socialism can utilize them, and market experiments must be conducted resolutely.

Deng's directive catalyzed the establishment of the Shanghai Stock Exchange (SSE) and Shenzhen Stock Exchange in 1990. On December 19, 1990, the SSE Composite Index (SSEC) was launched with a baseline value of 100 points across its initial 8 listed stocks. 

To rapidly deploy capital to state-owned enterprises (SOEs), market architects initially implemented an unadjusted total market-capitalization calculation methodology rather than a float-adjusted framework. The baseline SSEC formula was established as:

$$\text{SSEC} = \frac{\sum_{i=1}^{N} (P_{it} \times Q_{it})}{\sum_{i=1}^{N} (P_{i0} \times Q_{i0})} \times 100$$

where $P_{it}$ and $Q_{it}$ represent the current market price and total issued shares of constituent $i$, while $P_{i0}$ and $Q_{i0}$ represent the base-period parameters. Just as in the DJIA and S&P 500, the base divisor ($\sum P_{i0} \times Q_{i0}$) is modified whenever new constituents list on the exchange to prevent artificial point jumps and maintain continuous index series.

However, this structural design produced four major methodological distortions that historically anchored the headline SSEC around 3,000 points:

1. **Total Market-Cap Weighting & Non-Circulating Shares:** The original SSEC calculated corporate weights based on total issued shares ($Q_{it}$) rather than tradeable public float. Dominant state-owned enterprises (such as Industrial and Commercial Bank of China) received massive index weightings derived from large, non-circulating state equity blocks that never traded on the open market.
2. **Mega-Cap Drag:** Mature, slow-growing state-owned banks, energy producers, and industrial conglomerates dominated the baseline calculation. Stagnation in these heavy-weight traditional sectors suppressed overall index progress, masking operational gains achieved by smaller, fast-growing private enterprises.
3. **Over-valued IPO Inclusions ("Peak at Debut"):** Legacy index rules mandated adding newly listed IPO stocks to the index shortly after launch. Speculative retail enthusiasm routinely drove new issues (e.g., PetroChina) to extreme valuations on their trading debut. As these overpriced IPOs subsequently suffered multi-year price declines, their structural weight continuously dragged down the calculated index total.
4. **Inclusion of Distressed/ST Stocks and Exclusion of Tech Growth:** Legacy rules retained chronic loss-making Special Treatment (ST) companies within the index, creating a persistent performance drag. Concurrently, China's fastest-growing digital economy and consumer internet leaders (such as Alibaba, Tencent, and Meituan) listed on overseas exchanges or alternative boards, preventing the main-board index from capturing the economy's most dynamic growth sectors.

To fix these structural flaws, financial regulators implemented comprehensive index reforms between 2020 and 2026:

* **Single-Stock Weight Caps:** Capped the maximum index weight of any individual constituent at $\le 15\%$.
* **Delayed IPO Entry:** Postponed the inclusion of new IPO stocks into the index by 1 year post-listing to eliminate "peak at debut" price decay.
* **Exclusion of Distressed Assets:** Removed high-risk ST and non-performing stocks from the baseline calculation.
* **Tech Sector Integration:** Included the technology-focused STAR Market (Sci-Tech Innovation Board) directly into the benchmark index.

---

## 4. The 9.0% Real Return Paradox, Capital Allocation, and Investor Reality

Recalculating the multi-decade mathematical returns of the SSE Composite Index exposes a sharp divergence between headline perception and statistical reality. From its base of 100 points on December 19, 1990, to a closing level of 3,658 points in 2026 over a 36-year period, the SSEC generated the following return profile:

$$\text{Nominal Index Price CAGR} = 10.5\%$$
$$\text{Total Return (Dividend Reinvestment)} = 13.8\%$$
$$\text{Real Net Return (Inflation-Adjusted)} = 9.0\%$$

On an inflation-adjusted total return basis, Chinese equities delivered a 9.0% real compound annual return since 1990, outperforming the US equity market's historical 6.6% real compound return over its respective multi-decade evaluation periods.

Despite this performance, a large majority of retail participants experience net portfolio losses. This divergence is driven by structural entry timing, behavioral frictions, and underlying corporate governance incentives:

1. **Missed Early Surge Window:** The market's largest valuation expansion occurred between 1990 and 1993, when the SSEC surged 15-fold from 100 to 1,500 points. The vast majority of retail investors did not participate during this early phase, entering the market post-2005. For investors entering between 2005 and 2026, the average nominal index CAGR drops to ~5%.
2. **Behavioral Friction and Fee Decay:** Retail accounts frequently experience severe behavioral friction—buying aggressively during speculative market euphoria, panic selling at cyclical bottoms, and executing high-frequency trades. This excessive turnover generates substantial transaction fee decay, transforming a 9.0% real market compound return into negative real returns for retail accounts.
3. **Corporate Capital Allocation Mechanisms & Governance Incentives:** Multi-decade per-share owner wealth compounding depends fundamentally on corporate capital allocation strategy:
   * **The US Model ("Share Cannibalization"):** Through Warren Buffett's capital allocation lens, retiring tradeable shares below intrinsic value acts as an effective share cannibalization engine. By utilizing excess cash flow to repurchase and cancel outstanding float, corporations reduce their total share count. This increases per-share owner earnings and intrinsic value over time, driving per-share price appreciation even during periods of modest top-line revenue growth.
   * **The Historical A-Share Model & Shareholder Incentive Structure:** Historically, Chinese listed enterprises treated public equity markets primarily as capital-raising venues to fund asset expansion. Crucially, corporate governance incentives reinforced this preference: controlling and major state shareholders held non-circulating shares and could not participate in open-market share repurchases. Buying back tradeable public float did not put cash into the controlling shareholder's pocket. In contrast, paying out cash dividends distributed cash directly to major shareholders in exact proportion to their large equity holdings. Consequently, corporate managers favored cash dividend distributions or corporate capacity expansions over open-market share buybacks and share cancellations. Because tradeable float was rarely retired, per-share intrinsic value gains were diluted relative to gross corporate growth.

For value investors, headline index level movements are secondary to fundamental owner earnings, structural index reforms, corporate capital allocation mechanics, and disciplined behavioral execution. Sustainable wealth compounding occurs when purchasing durable, high-return businesses during periods of severe market pessimism, when crowd sentiment treats equity participation as irrational. To analyze underlying corporate earning power and evaluate true per-share intrinsic value across global markets, explore our open-source research reports on the DeepValues Research website or utilize the interactive valuation tools in the DeepValues application.

---

## Key numbers

* **0.25%**: Minimum broker commission rate mandated by the Buttonwood Agreement on Wall Street (1792).
* **40.94 points**: Launch value of the Dow Jones Industrial Average across 12 industrial stocks (May 26, 1896).
* **100 points**: Baseline index point value set for the DJIA upon expanding to 30 constituent stocks (October 1, 1928).
* **52,867.98 points**: DJIA index level recorded (October 1, 2026).
* **6.6%**: Nominal compound annual growth rate (CAGR) of the DJIA over 98 years (October 1, 1928 – October 1, 2026).
* **7.7%**: Nominal annual index price return of the S&P 500 index (1957 – 2026).
* **10.5%**: Total annual return of the S&P 500 with dividend reinvestment included (1957 – 2026).
* **6.6%**: Real annual return of the S&P 500 after deducting inflation (1957 – 2026).
* **500,000 shares**: Public stock issue size of Shanghai Feilo Acoustics (November 18, 1984).
* **601872**: SSE stock ticker code assigned to China Merchants Steam Navigation Company to commemorate its founding year (1872).
* **100 points**: Initial baseline value of the Shanghai Stock Exchange (SSE) Composite Index across 8 stocks (December 19, 1990).
* **3,658 points**: SSE Composite Index closing level (2026).
* **10.5%**: Nominal compound annual return of the SSE Composite Index without dividends (December 19, 1990 – 2026).
* **13.8%**: Total compound annual return of the SSE Composite Index with dividend reinvestment (December 19, 1990 – 2026).
* **9.0%**: Real compound annual return of the SSE Composite Index after adjusting for inflation (December 19, 1990 – 2026).
* **15x (100 to 1,500 points)**: Initial surge multiplier of the SSE Composite Index during its early phase (1990 – 1993).
* **5%**: Average annual nominal index return of the SSE Composite Index for investors entering post-2005 (2005 – 2026).
* **$\le 15\%$**: Maximum weight cap mandated for any single stock constituent under updated SSE Composite Index rules (2020 – 2026 reforms).
* **1 year**: Required listing period before new IPO stocks can be added to the SSE Composite Index (2020 – 2026 reforms).

---

## What would change our view

* **Widespread Adoption of Share Buybacks and Retained Share Cancellations:** Listed A-share companies shifting capital allocation strategies from capital raising/pure expansion to aggressively purchasing and cancelling tradeable float shares to elevate per-share value.
* **Broad-scale Listing and Re-weighting of High-Growth Technology and Service Leaders:** Re-balancing main-board A-share indices to prominently feature high-margin consumer internet, software, and service sector firms currently trading overseas or on alternative exchanges.
* **Sustained Disproportionate Retail Trading Volumes and Chasing Highs:** Persistence of extreme behavioral herd dynamics and frequent short-term trading by retail participants, eroding potential real index returns through transaction fee decay and poor entry timing.
* **Reversal or Stagnation of Index Methodology Rules:** Any rollback of the post-2020 reforms (such as relaxing the 15% constituent weight cap, re-admitting ST high-risk stocks, or shortening the 1-year waiting period for volatile new IPOs).

---

## Sources

Teacher Li Yongle - "Which Stock Market Makes More Money, US or China? Why Does the Dow Hit New Highs While the Shanghai Index Stays at 3000?" (YouTube Video Analysis)
