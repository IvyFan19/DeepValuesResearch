# A Comprehensive Guide to U.S. Options Taxation for the Active Trader

## Introduction

For the active options trader, mastering the intricacies of market dynamics, volatility, and strategy is only half the battle. The other, often overlooked, half is navigating the complex labyrinth of the U.S. tax code. Tax management is not a mere administrative task to be addressed at year-end; it is a critical and integrated component of profitable trading. A failure to understand and strategically apply tax rules can significantly erode returns, turning a profitable year on paper into a disappointing one after taxes. The Internal Revenue Service (IRS) has established a detailed and nuanced framework for the taxation of options, a framework that treats different types of options and different trading outcomes in fundamentally distinct ways.

This report provides an exhaustive, expert-level analysis of U.S. options taxation, with a particular emphasis on the considerations for options sellers. It is designed to equip the serious trader with the knowledge necessary to make tax-efficient decisions, ensure compliance, and ultimately preserve hard-earned capital. The analysis will begin by establishing the bedrock principles of capital gains taxation, which form the foundation for all subsequent rules. From there, it will dissect the tax treatment of the three potential outcomes for any option contract: being closed prior to expiration, expiring worthless, and being exercised or assigned.

The discussion will progress from the relatively straightforward rules for buying options to the more complex and varied tax consequences of selling them, including popular strategies like cash-secured puts and covered calls. Furthermore, the report will delve into advanced topics that are crucial for sophisticated traders, such as the stringent Wash Sale Rule, the critical distinction between equity options and tax-favored Section 1256 contracts, and the strategic implications of Trader Tax Status. Finally, it will provide practical guidance on how to translate complex trading activity into accurate reporting on the required IRS forms. By understanding these rules not just as a set of obligations but as a system of incentives and disincentives, the active trader can elevate their strategic approach from simply generating gross profits to maximizing after-tax returns.

## Section 1: The Foundation: Capital Gains Taxation in the U.S.

Before delving into the specific regulations governing options, it is essential to establish a firm understanding of the fundamental principles of capital gains taxation in the United States. The entire framework for options taxation is built upon this foundation. Every gain or loss from an options trade, with few exceptions, is ultimately characterized as a capital gain or loss, and its tax impact is determined by these core rules.

### 1.1 Short-Term vs. Long-Term Capital Gains

The single most important factor determining the tax rate applied to a profitable investment is its holding period. The U.S. tax code bifurcates capital gains into two distinct categories based on how long an asset was owned before being sold.

#### Holding Period Definition

The holding period is the length of time an asset is owned. For tax purposes, this period begins on the day *after* the asset is acquired and ends on the day it is sold. The distinction between short-term and long-term is precise:

-   **Short-Term Capital Gain/Loss:** Results from the sale of a capital asset held for **one year or less** (365 days or fewer).

-   **Long-Term Capital Gain/Loss:** Results from the sale of a capital asset held for **more than one year** (366 days or more).

This one-day difference can have a profound impact on an investor's tax liability due to the significant disparity in tax rates.

#### Tax Rate Disparity

The preferential treatment of long-term capital gains is a cornerstone of U.S. tax policy, designed to encourage long-term investment over short-term speculation.

-   **Short-Term Capital Gains:** These gains receive no special tax treatment. They are taxed at the investor's ordinary income tax rates, which are marginal and correspond to their tax bracket. For the 2024 and 2025 tax years, these rates range from 10% to 37%, depending on the investor's total taxable income and filing status. A short-term gain is, in effect, taxed the same as salary or wages.

-   **Long-Term Capital Gains:** These gains are taxed at preferential, lower rates. For the 2024 and 2025 tax years, there are three long-term capital gains tax brackets: 0%, 15%, and 20%. The applicable rate is determined by the investor's taxable income. For most investors, the rate is 15%. High-income earners pay 20%, while those in lower tax brackets may pay 0%.

This significant rate differential creates a powerful financial incentive to hold profitable assets for at least one year and a day. As will be discussed in later sections, many of the complex rules surrounding options taxation are specifically designed by the IRS to prevent traders from easily converting what would otherwise be short-term gains into these tax-favored long-term gains without bearing commensurate market risk. The structure of these regulations reveals a clear intent by the IRS: the preferential long-term rate is a reward for bearing the risk of capital loss for over a year, not merely for the passage of time on a risk-free position.

**Table 1: 2025 Capital Gains Tax Brackets (Long-Term vs. Short-Term)**

| Filing Status               | Taxable Income (Long-Term) | Long-Term Rate | Taxable Income (Short-Term/Ordinary) | Short-Term Rate |
|-----------------------------|----------------------------|----------------|--------------------------------------|-----------------|
| **Single**                  | $0 - $48,350               | 0%             | $0 - $11,600                         | 10%             |
|                             | $48,351 - $533,400         | 15%            | $11,601 - $47,150                    | 12%             |
|                             | &gt; $533,400              | 20%            | $47,151 - $100,525                   | 22%             |
|                             |                            |                | $100,526 - $191,950                  | 24%             |
|                             |                            |                | $191,951 - $243,725                  | 32%             |
|                             |                            |                | $243,726 - $609,350                  | 35%             |
|                             |                            |                | &gt; $609,350                        | 37%             |
| **Married, Filing Jointly** | $0 - $96,700               | 0%             | $0 - $23,200                         | 10%             |
|                             | $96,701 - $600,050         | 15%            | $23,201 - $94,300                    | 12%             |
|                             | &gt; $600,050              | 20%            | $94,301 - $201,050                   | 22%             |
|                             |                            |                | $201,051 - $383,900                  | 24%             |
|                             |                            |                | $383,901 - $487,450                  | 32%             |
|                             |                            |                | $487,451 - $731,200                  | 35%             |
|                             |                            |                | &gt; $731,200                        | 37%             |

*Note: Short-term capital gains are taxed at the same marginal rates as ordinary income. The income brackets are for the 2025 tax year, filed in 2026. Data sourced from.*

### 1.2 The Mechanics of Netting Gains and Losses

At the end of a tax year, an investor does not simply pay tax on each individual gain. The IRS requires a specific, multi-step netting process to determine the final net capital gain or loss.

1.  **Net Within Categories:** All short-term capital gains and short-term capital losses are netted against each other to arrive at a Net Short-Term Capital Gain or Loss.

2.  **Net Within Categories (cont.):** All long-term capital gains and long-term capital losses are netted against each other to arrive at a Net Long-Term Capital Gain or Loss.

3.  **Net the Results:** The net results of these two categories are then netted against each other.

This process can lead to several outcomes:

-   A net short-term gain and a net long-term gain (both are taxed at their respective rates).

-   A net short-term gain and a net long-term loss (the loss offsets the short-term gain).

-   A net short-term loss and a net long-term gain (the loss offsets the long-term gain).

-   A net loss in both categories, resulting in an overall net capital loss.

The final character of the gain or loss after this process is what determines the ultimate tax liability. For instance, using a net short-term loss to offset a net long-term gain is less tax-efficient than using it to offset a net short-term gain, because the short-term gain would have been taxed at a much higher rate.

### 1.3 The Capital Loss Limitation

If the netting process results in an overall net capital loss for the year, there is a limit to how much of that loss can be deducted against other forms of income, such as a salary or interest income.

-   **The $3,000 Rule:** An investor can deduct a maximum of **$3,000** of net capital loss against their ordinary income in any single tax year.

-   **Carryover Provision:** Any net capital loss that exceeds the $3,000 annual limit is not forfeited. It is carried forward to subsequent tax years indefinitely. In future years, this carryover loss can be used first to offset any capital gains. If a net loss still remains after offsetting gains, up to $3,000 of it can again be used to offset ordinary income, with any remainder carried forward again.

This limitation is a critical concept for traders, as a year with significant losses can create a tax asset (the loss carryover) that can be used to shield future gains from taxes for many years to come.

## Section 2: Tax Treatment of Buying Equity Options (Long Positions)

The tax consequences for an investor who buys an option (takes a long position) are generally more straightforward than those for an option seller. The tax treatment is determined by one of three possible outcomes for the contract: it is closed for a gain or loss, it expires worthless, or it is exercised.

### 2.1 Scenario 1: Closing a Long Option for a Gain or Loss

This is the most common outcome for a purchased option. The investor buys a call or put contract and, before it expires, sells the same contract to close the position and realize a profit or loss.

-   **Tax Treatment:** The transaction results in a capital gain or loss. The character of this gain or loss-whether it is short-term or long-term-is determined solely by the **holding period of the option contract itself**. If the option was held for one year or less, the result is a short-term capital gain or loss. If the option was held for more than one year, such as a Long-term Equity AnticiPation Security (LEAPS) option, the result is a long-term capital gain or loss.

-   **Example (Short-Term):** An investor believes shares of Apple Inc. (AAPL) will rise. On February 1, 2024, they buy one AAPL call option contract for a premium of $500. On June 20, 2024, the value of the option has increased, and they sell the same contract to close the position for $850.

    -   **Holding Period:** Less than one year.

    -   **Tax Consequence:** The investor realizes a **$350 short-term capital gain** ($850 proceeds - $500 cost basis). This gain will be taxed at their ordinary income rate.

-   **Example (Long-Term LEAPS):** An investor buys a LEAPS call option on Microsoft (MSFT) with a two-year expiration on March 15, 2024, for a premium of $2,000. On May 1, 2025 (more than one year later), they sell the LEAPS contract for $3,200.

    -   **Holding Period:** More than one year.

    -   **Tax Consequence:** The investor realizes a **$1,200 long-term capital gain** ($3,200 proceeds - $2,000 cost basis). This gain is eligible for the preferential 0%, 15%, or 20% tax rates.

### 2.2 Scenario 2: A Long Option Expires Worthless

If the underlying stock price does not move in the anticipated direction, the option may be "out-of-the-money" at expiration and become worthless.

-   **Tax Treatment:** When a purchased option expires worthless, the investor realizes a capital loss equal to the full premium paid for the contract, plus any commissions. For tax reporting purposes, the expiration date is treated as the "sale date," and the proceeds are $0. The character of the loss (short-term or long-term) is again determined by the holding period of the option. Given that most standard options have expirations of less than a year, these losses are almost always short-term.

-   **Example:** An investor buys one Meta Platforms (META) put option for a premium of $250, hoping the stock will fall. At the expiration date, META's stock price is trading above the put's strike price. The option expires worthless.

    -   **Holding Period:** Less than one year.

    -   **Tax Consequence:** The investor realizes a **$250 short-term capital loss**. This loss can be used to offset other capital gains.

### 2.3 Scenario 3: Exercising a Long Call or Put

The third possible outcome is that the investor exercises their right to either buy the underlying stock (with a call) or sell the underlying stock (with a put).

-   **Tax Treatment - The "No Immediate Tax Event" Rule:** A critical principle to understand is that the act of exercising an option is **not a taxable event in itself**. It does not immediately trigger a gain or loss on the option. Instead, the IRS treats it as a basis-adjustment event that merges the option transaction with the subsequent stock transaction. The tax consequences are deferred until the underlying stock position is ultimately sold.

-   **Exercising a Long Call:** When an investor exercises a call option to buy stock, the premium paid for the call is added to the purchase price of the shares to determine the total cost basis. The holding period for the newly acquired stock begins on the day *after* the exercise date.

    -   **Example:** An investor buys one NVIDIA (NVDA) call option with a strike price of $900 for a premium of $20 per share ($2,000 for the 100-share contract). Later, they exercise the option, buying 100 shares of NVDA.

        -   **Stock Purchase Cost:** $900 strike price \* 100 shares = $90,000.

        -   **Option Premium:** $2,000.

        -   **Adjusted Cost Basis:** $90,000 + $2,000 = **$92,000**.

        -   **Tax Consequence:** There is no immediate tax. The $92,000 cost basis will be used to calculate the capital gain or loss when the investor eventually sells the 100 shares of NVDA. The holding period for these shares starts the day after exercise.

-   **Exercising a Long Put (on previously owned stock):** When an investor already owns shares and exercises a put option to sell them, the premium paid for the put is subtracted from the sale proceeds of the stock. The resulting gain or loss is calculated based on the cost basis and holding period of the *stock*, not the put option.

    -   **Example:** An investor owns 100 shares of Tesla (TSLA) with a cost basis of $150 per share ($15,000 total). As a hedge, they buy one TSLA put with a strike price of $180 for a premium of $4 per share ($400 total). The stock price falls, and they exercise the put, selling their 100 shares at $180.

        -   **Stock Sale Proceeds (at strike):** $180 strike price \* 100 shares = $18,000.

        -   **Option Premium:** $400.

        -   **Adjusted Sale Proceeds:** $18,000 - $400 = **$17,600**.

        -   **Tax Consequence:** The taxable gain is $17,600 (adjusted proceeds) - $15,000 (stock cost basis) = **$2,600**. The character of this gain (long-term or short-term) depends on how long the investor held the TSLA shares, not the put.

This treatment of exercised options demonstrates a "substance over form" approach by the IRS. The tax system recognizes that the premium paid for the option is an integral cost of the overall transaction to acquire or dispose of the underlying stock. By rolling the option's cost into the stock's basis or proceeds, the IRS avoids creating unnecessarily complex and separate tax events. This ensures that the final tax calculation accurately reflects the total economic profit or loss of the entire investment journey, from the first dollar spent on the option to the final dollar received from the stock sale.

## Section 3: The Trader's Focus: Tax Treatment of Selling Equity Options (Short Positions)

The taxation of short option positions-where a trader sells or "writes" a contract to open a position-is significantly more complex and nuanced than for long positions. This is the primary area of focus for income-generating strategies, and understanding these rules is paramount. The tax treatment hinges on how the seller's obligation is resolved: by closing the position, by letting it expire, or by being assigned.

### 3.1 The Universal Rule for Closing/Expiring Short Options

There is one overarching rule that simplifies a large portion of short option taxation. Unlike long options, where the holding period of the contract determines the character of the gain or loss, the outcome for a short option that does *not* result in assignment is always the same.

-   **Core Concept:** Any gain or loss realized from a short option position that is either **closed out** (bought back before expiration) or **expires worthless** is **always treated as a short-term capital gain or loss**. This is true regardless of how long the option contract was open, even if it was a LEAPS option held for over a year.

The rationale behind this rule is that the writer of an option is undertaking an obligation, not holding a capital asset. The concept of a holding period applies to assets that can appreciate over time. The premium received by an option writer is immediate income, and the taxable event occurs when the obligation tied to that income is extinguished.

This "always short-term" rule has significant strategic implications. It means that income generated purely from selling option premium that expires or is closed for a profit will be taxed at the trader's highest marginal ordinary income rate. This creates a notable tax drag for traders focused on premium collection compared to buy-and-hold investors who can benefit from lower long-term capital gains rates. This structural tax inefficiency makes it strategically compelling for traders to consider conducting such strategies in tax-advantaged accounts like an IRA, where gains are tax-deferred or tax-free, or to use specialized products like Section 1256 contracts (covered in Section 4.3) that offer more favorable tax treatment.

### 3.2 The Cash-Secured Put

A cash-secured put is a strategy where a trader sells a put option on a stock they are willing to own at the strike price. The position is "secured" by setting aside enough cash to purchase the 100 shares per contract if assignment occurs. The economic goal is either to collect the premium as income or to acquire the stock at an effective price below the current market price.

#### Scenario A: The Put Expires Worthless (Out-of-the-Money)

This is the ideal outcome for a trader whose sole goal is income generation.

-   **Mechanism:** The underlying stock price remains above the put's strike price through the expiration date. The option buyer has no incentive to exercise, and the contract expires worthless.

-   **Tax Treatment:** The entire premium received by the seller is recognized as a **short-term capital gain** in the tax year that the option expires.

-   **Example:** On May 10, a trader sells one Advanced Micro Devices (AMD) put option with a $150 strike price and a June expiration date, receiving a premium of $3 per share, or $300 total. On the expiration date in June, AMD stock is trading at $155 per share. The put is out-of-the-money and expires worthless.

    -   **Tax Consequence:** The trader has a **$300 short-term capital gain** for the year.

#### Scenario B: Closing the Put for a Profit or Loss (Buy to Close)

A trader may decide to close their position before expiration to lock in a profit or cut a loss.

-   **Mechanism:** The trader executes a "buy to close" order, purchasing the same put option they initially sold.

-   **Tax Treatment:** The difference between the premium originally received (from the "sell to open" order) and the premium paid to close the position (the "buy to close" order) is a **short-term capital gain or loss**.

-   **Example (Profit):** A trader sells one AMD $150 put for a $300 premium. A week later, AMD's stock price has risen, and the value of the put option has decreased to $50. The trader buys the put back for $50 to close the position.

    -   **Tax Consequence:** The trader realizes a **$250 short-term capital gain** ($300 received - $50 paid).

-   **Example (Loss):** A trader sells one AMD $150 put for a $300 premium. A week later, AMD's stock price has fallen, and the value of the put option has increased to $450. Fearing further losses, the trader buys the put back for $450 to close the position.

    -   **Tax Consequence:** The trader realizes a **$150 short-term capital loss** ($300 received - $450 paid).

#### Scenario C: Assignment - Being Forced to Buy the Stock

This outcome occurs if the stock price falls below the strike price and the option holder exercises their right. The put seller is now obligated to buy the stock.

-   **Mechanism:** The stock price is below the strike price at or near expiration, and the put seller receives an assignment notice from their broker, resulting in the purchase of 100 shares of the stock at the strike price.

-   **Tax Treatment - The "Cost Basis Reduction" Rule:** The assignment of a short put is **not an immediate taxable event**. Instead, the premium received from selling the put is used to **reduce the cost basis** of the 100 shares the trader was forced to buy. The holding period for these newly acquired shares begins on the day *after* the assignment date. The original short put transaction itself is not reported as a separate gain or loss on tax forms; its financial impact is fully absorbed into the stock's basis.

-   **Example:** A trader sells one AMD $150 put for a $300 premium. At expiration, AMD is trading at $140 per share. The trader is assigned and must buy 100 shares of AMD at the strike price of $150.

    -   **Cash Outlay:** $150 strike price \* 100 shares = $15,000.

    -   **Premium Received:** $300.

    -   **Adjusted Cost Basis:** $15,000 - $300 = **$14,700** (or $147 per share).

    -   **Tax Consequence:** There is no immediate tax due. The trader now owns 100 shares of AMD with a cost basis of $14,700. The tax event is deferred until they eventually sell these shares. If they sell the shares a month later for $16,000, they will have a short-term capital gain of $1,300 ($16,000 - $14,700).

### 3.3 The Covered Call

The covered call strategy involves selling a call option against at least 100 shares of an underlying stock that the trader already owns. It is a popular strategy for generating income from a stock holding that is expected to remain stable or rise modestly.

#### Scenario A: The Call Expires Worthless (Out-of-the-Money)

This is the most common desired outcome for covered call writers.

-   **Mechanism:** The underlying stock price remains below the call's strike price through the expiration date. The contract expires worthless.

-   **Tax Treatment:** The entire premium received is recognized as a **short-term capital gain**, regardless of how long the underlying stock has been held.

-   **Example:** An investor owns 100 shares of Microsoft (MSFT). On July 1, they sell one MSFT call option with a $450 strike price and an August expiration, receiving a premium of $5 per share, or $500 total. On the expiration date, MSFT is trading at $440 per share. The call expires worthless.

    -   **Tax Consequence:** The investor has a **$500 short-term capital gain**. This does not affect the cost basis or holding period of their 100 MSFT shares.

#### Scenario B: Closing the Call for a Profit or Loss (Buy to Close)

The investor may choose to buy back the call to lock in a gain on the option or to free up their shares for sale.

-   **Mechanism:** The investor executes a "buy to close" order for the same call option they sold.

-   **Tax Treatment:** The difference between the premium received and the premium paid to close is a **short-term capital gain or loss**.

-   **Example:** An investor sells one MSFT $450 call for a $500 premium. Two weeks later, the option's value has decayed to $100. They buy it back for $100 to close the position.

    -   **Tax Consequence:** The investor realizes a **$400 short-term capital gain** ($500 received - $100 paid).

#### Scenario C: Assignment - Having Your Stock Called Away

This occurs if the stock price rises above the strike price and the call buyer exercises their right to buy the stock.

-   **Mechanism:** The stock price is above the strike price, and the call seller is assigned, forcing them to sell their 100 shares at the strike price.

-   **Tax Treatment - The "Adjusted Sales Proceeds" Rule:** When a covered call is assigned, the premium received from selling the call is **added to the strike price** to calculate the total, or "adjusted," sales proceeds for the stock. A capital gain or loss is then calculated on the *stock*. The character of this gain or loss (short-term or long-term) is determined by the **holding period of the stock itself**, provided the option was a "qualified covered call" (see Section 4.2).

-   **Example:** An investor owns 100 shares of MSFT that they purchased on January 10, 2022, for $300 per share (a total cost basis of $30,000). On August 1, 2024, they sell one MSFT call with a $450 strike price for a $500 premium. Later that month, MSFT stock rises to $460 per share, and their shares are called away.

    -   **Proceeds from Strike:** $450 strike price \* 100 shares = $45,000.

    -   **Premium Received:** $500.

    -   **Adjusted Sales Proceeds:** $45,000 + $500 = **$45,500**.

    -   **Tax Consequence:** The taxable gain is $45,500 (adjusted proceeds) - $30,000 (stock cost basis) = **$15,500**. Because the MSFT shares were held for more than one year (from Jan 2022 to Aug 2024), this is a **long-term capital gain**.

The IRS's treatment of assignment for both puts and calls reveals a consistent principle: the assignment is not viewed as the closing of an option trade but as the final step in a stock transaction. The option premium is fundamentally a negotiated price adjustment. For an assigned put, it lowers the effective purchase price of the stock. For an assigned call, it increases the effective selling price. This approach prevents the creation of separate, and often mismatched, tax events (e.g., a short-term gain on the premium and a long-term loss on the stock) and instead integrates them into a single, economically coherent taxable event tied to the underlying shares.

**Table 2: Tax Treatment Summary for Selling Equity Options**

| Outcome                             | Short Put (e.g., Cash-Secured Put)                                                                                                                              | Short Call (e.g., Covered Call)                                                                                                                                         |
|-------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Option Expires Worthless**        | **Short-term capital gain** equal to the premium received.                                                                                                      | **Short-term capital gain** equal to the premium received.                                                                                                              |
| **Option is Closed (Buy to Close)** | **Short-term capital gain or loss** equal to the net difference between premium received and premium paid.                                                      | **Short-term capital gain or loss** equal to the net difference between premium received and premium paid.                                                              |
| **Option is Assigned**              | **No immediate tax event.** The premium received **reduces the cost basis** of the stock purchased. The stock's holding period begins the day after assignment. | **Taxable event on the stock.** The premium received **increases the sales proceeds** of the stock sold. The gain/loss character depends on the stock's holding period. |

## Section 4: Advanced Tax Considerations and Special Rules

Beyond the basic tax treatments for buying and selling options, several advanced rules can have a significant and often unexpected impact on a trader's tax liability. These regulations, established under specific sections of the Internal Revenue Code, are designed to prevent certain tax avoidance strategies and to provide a distinct tax regime for certain types of financial instruments. Active traders must have a working knowledge of these rules to manage their positions effectively and avoid costly errors.

### 4.1 The Wash Sale Rule (Section 1091)

The Wash Sale Rule is one of the most important and frequently encountered regulations for active traders. Its purpose is to prevent investors from claiming a tax loss on a security while effectively maintaining their economic position in that same security.

-   **Defining the Rule:** A wash sale occurs if an investor sells a security (including a stock or an option) at a loss and, within a 61-day window-spanning from 30 days before the sale to 30 days after the sale-they acquire a "substantially identical" security. The rule is broad in its application. It is triggered not only by buying the identical security but also by acquiring a contract or option to buy that security. Furthermore, the rule applies across all of an individual's accounts, including taxable brokerage accounts and IRAs, and even extends to transactions made by their spouse.

-   **Consequences of a Wash Sale:** When a wash sale is triggered, the following occurs:

    1.  **Loss Disallowed:** The loss from the initial sale is not deductible for tax purposes in the current year. The tax benefit is deferred, not permanently lost (unless the replacement security is purchased in an IRA, in which case the loss is permanently forfeited because basis cannot be adjusted in an IRA).

    2.  **Basis Adjustment:** The disallowed loss is added to the cost basis of the newly acquired, "replacement" security. This adjustment effectively transfers the disallowed loss to the new position, allowing it to be recognized in the future when the replacement security is sold.

    3.  **Holding Period Tacking:** The holding period of the original security that was sold at a loss is added to the holding period of the replacement security. This can be beneficial, as it might allow a subsequent sale of the replacement security to qualify for long-term capital gains treatment sooner than it otherwise would.

-   **The Ambiguity of "Substantially Identical" for Options:** The primary challenge in applying the wash sale rule to options is the IRS's lack of a clear, objective definition for "substantially identical." The determination is based on the specific "facts and circumstances" of each case.

    -   **General Interpretation:** For options on the same underlying stock, the common practice among brokers and tax professionals is that contracts with **different strike prices or different expiration dates are generally *not* considered substantially identical**. This interpretation allows a trader, for example, to sell a losing AAPL $170 call expiring in June and immediately buy an AAPL $175 call expiring in July without triggering a wash sale. However, it is crucial to recognize that this is an industry convention, not a formal IRS safe harbor.

    -   **Economic Equivalence:** The IRS could potentially challenge this convention in extreme cases. For instance, selling a stock at a loss and immediately buying a very deep-in-the-money call option on that same stock could be deemed a wash sale. The rationale would be that the deep-in-the-money call has a delta approaching 1.0 and behaves almost identically to the underlying stock, making it economically equivalent. Similarly, selling a losing call option and buying another with a nearly identical strike and an expiration date only a week apart might be viewed as substantially identical. Traders should exercise caution when replacing a losing position with one that has a nearly identical risk profile.

### 4.2 Qualified vs. Unqualified Covered Calls

The tax treatment of a covered call strategy can be affected by the specific characteristics of the call option that is sold. The IRS has established rules to differentiate between "qualified" and "unqualified" covered calls, primarily to prevent investors from using options to manipulate the holding period of their stock to achieve long-term capital gains status without bearing long-term risk.

-   **Qualified Covered Call (QCC) Criteria:** While the rules are complex, a covered call is generally considered "qualified" if it meets certain criteria. The most important are that the option must have **more than 30 days remaining until expiration** when it is written, and its strike price must **not be "deep-in-the-money"**. A deep-in-the-money call is one with a strike price significantly below the current stock price.

-   **Tax Impact of Writing a QCC:** When an investor writes a qualified covered call, the holding period of their underlying stock continues to accrue without interruption. If the stock is later called away, the gain or loss is characterized as long-term or short-term based on the stock's original, uninterrupted holding period.

-   **Tax Impact of Writing an Unqualified Call:** If an investor writes an unqualified covered call (e.g., a deep-in-the-money call or one with less than 30 days to expiration), the tax consequences are more punitive. The holding period of the underlying stock is **suspended** for the entire time that the short call position is open.

    -   **Example:** An investor buys 100 shares of stock on January 15. On December 1 (10.5 months later), they write a deep-in-the-money covered call against the shares. The call remains open for 45 days. During this 45-day period, the stock's holding period is frozen at 10.5 months. It does not continue to accrue. If the stock is sold immediately after the call position is closed, the gain will be short-term. The unqualified call prevented the holding period from crossing the critical one-year threshold, potentially converting a 15% long-term tax into a 32% short-term tax.

### 4.3 Section 1256 Contracts - A Different Tax World

A special category of financial instruments, defined under Section 1256 of the tax code, receives a unique and often highly advantageous tax treatment. For options traders, this category is critically important as it includes options on broad-based stock market indexes.

-   **Definition:** Section 1256 contracts include regulated futures contracts, foreign currency contracts, and, most relevantly for options traders, **non-equity options**. These are options on broad-based stock indexes, such as the S&P 500 Index (SPX), the Nasdaq 100 Index (NDX), the Russell 2000 Index (RUT), and the CBOE Volatility Index (VIX). It is essential to distinguish these from options on Exchange Traded Funds (ETFs) that track these indexes, such as SPY, QQQ, or IWM. Options on ETFs are treated as standard equity options, not Section 1256 contracts.

This distinction gives rise to one of the most powerful tax-planning opportunities available to traders. The economic exposure of trading options on SPX versus SPY is nearly identical, but their tax treatment is profoundly different. This is not merely a technicality but a deliberate policy choice, likely intended to provide favorable conditions and encourage liquidity in the broad market index and futures markets that are central to institutional hedging. For the individual trader, this creates a clear strategic imperative: for any strategy involving a broad market index, using the Section 1256 product (e.g., SPX) is almost always more tax-efficient than using its non-1256 ETF equivalent (e.g., SPY).

-   **The 60/40 Rule:** This is the primary benefit of Section 1256 contracts. Regardless of how long a position is held-whether for ten minutes or ten months-all capital gains and losses are automatically treated as **60% long-term and 40% short-term**. This blended rate provides a significant tax reduction for active traders whose gains would otherwise be 100% short-term.

-   **The Mark-to-Market Rule:** Section 1256 contracts are subject to year-end mark-to-market accounting. This means that all open positions held on December 31st are treated as if they were sold for their fair market value on the last business day of the year. The resulting unrealized ("marked-to-market") gain or loss must be reported on that year's tax return using the 60/40 rule. The cost basis of the position is then adjusted up or down to this year-end value for the purposes of calculating gain or loss in the following year.

While this rule simplifies year-end reporting by eliminating the need to track individual holding periods, it can create a significant cash flow challenge known as "phantom income." A trader could have a large unrealized gain on paper at year-end, owe substantial real cash in taxes on that gain, and then see the position reverse into a loss in the new year. Although a corresponding loss can be claimed in the new tax year, the trader must have the liquidity to pay the tax on the phantom gain in the interim.

-   **Wash Sale Exemption:** Section 1256 contracts are **explicitly exempt** from the wash sale rule. This provides traders with much greater flexibility to manage losing positions without being concerned about the 61-day window.

-   **Comparative Example (SPX vs. SPY):** Consider a trader in the 32% marginal tax bracket who realizes a $10,000 profit from a day trade.

    -   **Trade on SPY (ETF Option):** This is an equity option. The entire $10,000 is a short-term capital gain.

        -   Tax Liability: $10,000 \* 32% = $3,200.

    -   **Trade on SPX (Index Option - Sec. 1256):** The gain is subject to the 60/40 rule.

        -   Long-Term Portion: $10,000 \* 60% = $6,000. Taxed at 15%.

        -   Short-Term Portion: $10,000 \* 40% = $4,000. Taxed at 32%.

        -   Tax Liability: ($6,000 \* 15%) + ($4,000 \* 32%) = $900 + $1,280 = $2,180.

    -   **Tax Savings:** By choosing the Section 1256 contract, the trader saves **$1,020** in taxes on the exact same economic outcome.

**Table 3: Equity Options vs. Section 1256 Contracts - A Tax Comparison**

| Feature                          | Equity Options (e.g., SPY, AAPL)                                                                 | Section 1256 Contracts (e.g., SPX, VIX)                                                                                 |
|----------------------------------|--------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| **Underlying Asset**             | Individual stocks or ETFs that hold stocks.                                                      | Broad-based stock market indexes, commodities, futures.                                                                 |
| **Governing Rule**               | Standard capital gains rules.                                                                    | IRS Section 1256.                                                                                                       |
| **Tax Rate Treatment**           | Based on holding period. Most trading gains are 100% short-term, taxed at ordinary income rates. | **60/40 Rule:** All gains/losses are 60% long-term and 40% short-term, regardless of holding period.                    |
| **Year-End Reporting**           | Gains/losses are realized only when a position is closed.                                        | **Mark-to-Market Rule:** Open positions are treated as closed on Dec. 31, and unrealized gains/losses must be reported. |
| **Wash Sale Rule Applicability** | **Yes**, the wash sale rule applies to equity options.                                           | **No**, Section 1256 contracts are exempt from the wash sale rule.                                                      |

## Section 5: Reporting Your Trades to the IRS

Translating a year's worth of complex trading activity into the proper format for the IRS is a critical final step. The process involves understanding the information provided by your broker and accurately transcribing and, where necessary, adjusting it on specific tax forms. The primary forms involved are Form 1099-B, Form 8949, and Schedule D.

### 5.1 Decoding Your Form 1099-B

At the beginning of each year, your brokerage firm will provide you with Form 1099-B, *Proceeds From Broker and Barter Exchange Transactions*. This form is a summary of your gross proceeds from all sales of securities, including options, during the prior year. A copy is also sent to the IRS.

-   **Purpose and Content:** The 1099-B serves as the starting point for your tax reporting. Key information includes:

    -   **Description of Property (Box 1a):** Identifies the security sold.

    -   **Date Acquired (Box 1b) and Date Sold (Box 1c):** Determines the holding period.

    -   **Proceeds (Box 1d):** The gross amount received from the sale, before commissions.

    -   **Cost or Other Basis (Box 1e):** The amount paid for the security.

    -   **Basis Reported to IRS (Box 12):** A crucial checkbox indicating whether the broker has also reported the cost basis figure to the IRS. This affects how you report the transaction.

-   **The Broker's Limitation and Taxpayer Responsibility:** It is imperative to understand that the Form 1099-B provided by your broker may not be entirely correct for tax purposes, especially concerning options transactions. For example, in the case of an assigned short put, the broker may report a cost basis equal to the strike price paid for the shares, failing to account for the basis reduction from the option premium. Similarly, for an assigned covered call, the proceeds may not reflect the addition of the premium. The ultimate legal responsibility for reporting the correct cost basis, proceeds, and resulting gain or loss rests solely with the **taxpayer**.

The IRS reporting system is implicitly designed as a system of checks and balances. The IRS computers will attempt to match the proceeds reported by brokers on Form 1099-B with the proceeds reported by taxpayers on their returns. However, the IRS provides a specific mechanism-the adjustment columns on Form 8949-for the taxpayer to correct the broker's data and apply the complex tax rules accurately. The 1099-B is a starting point, not the final word. Failure to make the necessary adjustments on Form 8949 constitutes an incorrect tax filing.

### 5.2 Introduction to Form 8949 and Schedule D

The reporting of capital gains and losses follows a clear hierarchy, flowing from detailed transactions to a final summary.

-   **Form 8949, *Sales and Other Dispositions of Capital Assets*:** This is the "detail" form. Each individual sale of a capital asset, including each closed or expired option trade, is listed on its own line on this form. It is used to reconcile the amounts on your 1099-B with the amounts you are reporting. The form is divided into two parts: Part I for short-term transactions and Part II for long-term transactions.

-   **Schedule D, *Capital Gains and Losses*:** This is the "summary" form. The subtotals of gains and losses from all your Form 8949 pages are carried over to Schedule D. On Schedule D, these totals are netted together to calculate your final net short-term and net long-term capital gain or loss for the year. This final figure from Schedule D is then carried over to your main Form 1040 tax return.

The standard reporting flow is: **Form 1099-B (from broker) → Form 8949 (details entered by taxpayer) → Schedule D (summary calculated by taxpayer) → Form 1040**.

### 5.3 Step-by-Step Reporting Examples

The following examples illustrate how to report common option-selling scenarios on Form 8949.

#### Scenario A: Reporting an Expired Short Call

A trader sells one XYZ call option for a $200 premium. The option expires worthless.

-   **Form/Part:** Form 8949, Part I (Short-Term).

-   **Box to Check:** Check Box C if the transaction is not reported on your 1099-B (some brokers do not report expired short options). If it is on the 1099-B, check Box A or B as appropriate.

-   **Column (a) Description of property:** 1 XYZ Call

-   **Column (b) Date acquired:** Enter the date you sold (wrote) the call option.

-   **Column (c) Date sold or disposed of:** Enter the date the option expired.

-   **Column (d) Proceeds (sales price):** Enter the premium you received, $200.

-   **Column (e) Cost or other basis:** Enter $0.

-   **Column (f) Code(s):** Leave blank unless an adjustment is needed.

-   **Column (g) Amount of adjustment:** Leave blank.

-   **Column (h) Gain or (loss):** $200.

This entry correctly reports the $200 premium as a short-term capital gain, consistent with the tax rules.

#### Scenario B: Reporting an Assigned Cash-Secured Put (and Subsequent Stock Sale)

A trader sells one ABC put with a $50 strike for a $150 premium. The trader is assigned and forced to buy 100 shares of ABC at $50. A few months later, they sell the 100 shares for $5,500.

This is a two-step process for tax reporting.

**Step 1: The Assignment Itself** As established, the assignment of the short put is **not reported on Form 8949** at the time of assignment. It is a basis adjustment event. The trader must keep a record of this transaction to correctly calculate the basis of the stock.

-   Stock Purchase Price: $50 strike \* 100 shares = $5,000

-   Premium Received: $150

-   **Correct Tax Basis of Stock:** $5,000 - $150 = $4,850

**Step 2: Reporting the Sale of the Stock** When the 100 shares of ABC are sold for $5,500, this transaction must be reported on Form 8949. The broker's 1099-B will likely report the basis as $5,000. The trader must correct this.

-   **Form/Part:** Form 8949, Part I (Short-Term, since the stock was held for only a few months).

-   **Box to Check:** Check Box A, as the transaction was reported on Form 1099-B with basis reported to the IRS (even though the basis is incorrect).

-   **Column (a) Description of property:** 100 Shares ABC

-   **Column (b) Date acquired:** Enter the date of the put assignment.

-   **Column (c) Date sold or disposed of:** Enter the date the stock was sold.

-   **Column (d) Proceeds (sales price):** Enter $5,500 (as shown on 1099-B).

-   **Column (e) Cost or other basis:** Enter $5,000 (as shown on 1099-B).

-   **Column (f) Code(s):** Enter code **B** to signify that the basis reported by the broker is incorrect.

-   **Column (g) Amount of adjustment:** Enter **-$150**. This negative adjustment corrects the basis from the broker's $5,000 down to the true tax basis of $4,850.

-   **Column (h) Gain or (loss):** $650. This is calculated as (d) - (e) + (g), or $5,500 - $5,000 + (-$150) = $650. This correctly reflects the gain based on the true tax basis ($5,500 - $4,850 = $650).

This example highlights the critical function of columns (f) and (g) on Form 8949. They are the official mechanism for taxpayers to override incorrect broker-reported data and ensure their tax liability is calculated correctly based on the specific rules for options assignment.

## Section 6: Strategic Tax Planning for Options Traders

For traders who engage in options trading as a significant part of their financial activity, moving beyond rule compliance to strategic tax planning is essential. This involves considering special tax statuses and elections that can fundamentally alter how trading profits and losses are treated by the IRS. These are high-level decisions with significant consequences and should only be made in consultation with a qualified tax professional.

### 6.1 Investor vs. Trader Tax Status (TTS)

The IRS makes a distinction between an "investor" and a "trader." While most individuals who buy and sell securities are considered investors, some may qualify for Trader Tax Status (TTS).

-   **Definition and Criteria:** The distinction is not based on self-declaration but on a strict set of criteria. To be considered engaged in the business of trading, an individual must demonstrate that their activity is **substantial, continuous, and regular**. The primary objective must be to profit from **daily market movements** in the prices of securities, rather than from long-term appreciation, dividends, or interest. The bar for meeting these criteria is exceptionally high; trading as a part-time activity or a hobby, even if frequent, is not sufficient. The IRS considers it akin to running a full-time business.

-   **Benefits of TTS:** The primary benefit of qualifying for TTS is the ability to treat trading-related expenses as business expenses. An investor can only take a limited itemized deduction for investment interest expense. A trader with TTS, however, can deduct a wide range of expenses on Schedule C, *Profit or Loss from Business*. These can include costs for specialized software, data feeds, computer hardware, home office expenses, and educational materials. These deductions reduce the trader's overall taxable income. It is important to note that commissions and fees on trades are not deductible as business expenses; they are capitalized into the cost basis or deducted from the proceeds of the securities sold, for both investors and traders.

### 6.2 The Section 475 Mark-to-Market Election

Qualifying for TTS opens the door to a far more powerful and transformative tax election: the Section 475(f) mark-to-market election. This is a formal election that must be made by the original due date of the tax return for the year *prior* to the year the election is to take effect.

-   **Consequences of the Election:** Making a valid Section 475 election fundamentally changes the tax treatment of trading activity:

    1.  **Ordinary Gain/Loss Treatment:** All gains and losses from the trading business are no longer treated as capital gains and losses. Instead, they are treated as **ordinary income and losses**.

    2.  **Capital Loss Limitation Removed:** The most significant benefit of this change is the removal of the $3,000 annual capital loss limitation. With a Section 475 election, trading losses are ordinary losses and can be used to offset other ordinary income (like a spouse's salary) without limit. This provides a crucial safety net for professional traders who could otherwise face a catastrophic, non-deductible loss in a bad year.

    3.  **Wash Sale Rule Exemption:** Securities subject to the mark-to-market election are exempt from the wash sale rule.

    4.  **Year-End Mark-to-Market:** Similar to Section 1256 contracts, all open trading positions must be marked-to-market at year-end, with the unrealized gain or loss reported as ordinary income or loss for that year.

-   **Strategic Implications and Risks:** The decision to pursue TTS and make a Section 475 election represents a fundamental shift from treating trading as a capital asset activity to a business activity. This is a high-stakes decision with consequences that are difficult to reverse. The benefit of unlimited loss deduction is traded against the forfeiture of all preferential capital gains tax rates.

This trade-off is not suitable for all traders. A trader whose strategy sometimes generates long-term capital gains (e.g., from holding assigned stock for over a year) or who benefits significantly from the 60/40 blended rate on Section 1256 contracts would see those tax advantages eliminated. All profits, regardless of their source or holding period, would be taxed at their highest marginal ordinary income rate. Therefore, this election is typically only appropriate for a very specific type of trader: one whose strategy generates almost exclusively short-term gains and for whom the risk of a large, non-deductible capital loss is a greater concern than the potential benefit of ever achieving preferential tax rates on gains. It is a strategic choice that prioritizes risk management over tax rate optimization.

## Conclusion

The tax implications of U.S. options trading are intricate and demand careful attention from any serious market participant. As this analysis has demonstrated, a trader's after-tax return is not merely a function of their trading acumen but also of their understanding and application of a complex set of tax regulations. Several critical takeaways emerge as essential knowledge for every options trader.

First, the tax treatment of short option positions that are closed or expire is fundamentally different from that of long positions. The gain or loss on these transactions is **always short-term**, regardless of the holding period, subjecting income-focused premium sellers to taxation at higher ordinary income rates. This creates a structural tax headwind that must be managed strategically.

Second, the event of assignment is not a taxable event in itself but rather a **basis-adjustment event**. For an assigned short put, the premium received reduces the cost basis of the acquired stock. For an assigned covered call, the premium increases the sales proceeds of the stock sold. This rule defers the tax consequence and integrates the option's economics into the underlying stock transaction, a principle that is crucial for accurate tax reporting.

Third, a profound and often overlooked distinction exists between equity options (e.g., on SPY) and Section 1256 index options (e.g., on SPX). The latter are subject to the highly favorable **60/40 rule**, which treats all gains and losses as 60% long-term and 40% short-term, regardless of the holding period. For traders active in broad market indexes, choosing the appropriate trading vehicle can lead to substantial tax savings.

Finally, the ultimate responsibility for accurate tax reporting lies with the taxpayer, not their broker. The broker-provided Form 1099-B is a starting point, but it often fails to account for the nuanced basis adjustments required by options assignments. The taxpayer must utilize **Form 8949** to correct this data and report the true taxable gain or loss to the IRS.

Navigating this landscape requires diligence, meticulous record-keeping, and a proactive approach to tax planning. The rules are complex, and their application can vary based on an individual's specific trading patterns and financial situation. Therefore, while this report provides a comprehensive educational framework, it is not a substitute for personalized professional advice. All traders are strongly encouraged to consult with a qualified tax professional who has experience with securities and options trading to ensure compliance and optimize their tax strategy.

#### Works cited

1\. A Guide to the Capital Gains Tax Rate: Short-term vs. Long-term Capital Gains Taxes - TurboTax Tax Tips & Videos, https://turbotax.intuit.com/tax-tips/investments-and-taxes/guide-to-short-term-vs-long-term-capital-gains-taxes-brokerage-accounts-etc/L7KCu9etn 2. Short vs. Long-Term Capital Gains & Tax Rates - Carta, https://carta.com/learn/equity/stock-options/taxes/capital-gains/ 3. Long-Term vs. Short-Term Capital Gains - Investopedia, https://www.investopedia.com/articles/personal-finance/101515/comparing-longterm-vs-shortterm-capital-gain-tax-rates.asp 4. Taxation \| optionstax - The Options Tax Guy, https://www.optionstaxguy.com/taxation 5. 2025 Capital Gains Tax Calculator - Long-Term & Short-Term Gains - SmartAsset.com, https://smartasset.com/investing/capital-gains-tax-calculator 6. 2024-2025 Long-Term Capital Gains Tax Rates \| Bankrate, https://www.bankrate.com/investing/long-term-capital-gains-tax/ 7. Understanding Tax Rules for Call and Put Options in the U.S. - Investopedia, https://www.investopedia.com/articles/active-trading/053115/tax-treatment-call-put-options.asp 8. How Options Are Taxed - SmartAsset.com, https://smartasset.com/taxes/taxes-on-options-trading 9. Taxes on options \| Options \| Derivatives \| Investment vehicle characteristics \| Achievable Series 65, https://app.achievable.me/study/finra-series-65/learn/investment-vehicle-characteristics-derivatives-options-taxes-on-options 10. How Are Options Taxed: All You Need to Know - tastylive, https://www.tastylive.com/concepts-strategies/how-are-options-taxed 11. Taxes on options \| Taxes \| Achievable Series 7 - Exam catalog, https://app.achievable.me/study/finra-series-7/learn/taxes-taxes-on-options 12. Options - Tax Portal FAQ, https://www.taxportalfaq.com/options 13. Tax Implications When You Exercise Stock Options \| Eqvista, https://eqvista.com/stock-option-taxation/tax-implications-exercise-stock-options/ 14. What if I have expired options? - FAQ 1491 - FreeTaxUSA, https://www.freetaxusa.com/answer/1491 15. How Are Options Taxed? \| Charles Schwab, https://www.schwab.com/learn/story/how-are-options-taxed 16. Tax Implications of Covered Calls - Fidelity Investments, https://www.fidelity.com/learning-center/investment-products/options/tax-implications-covered-calls 17. OPTIONS TRADER TAXES - TradeLog, https://tradelog.com/education/options-trader-taxes/ 18. What is a cash-secured put? - Fidelity Investments, https://www.fidelity.com/learning-center/smart-money/cash-secured-put 19. Cash-Secured Put - The Options Industry Council, https://www.optionseducation.org/strategies/all-strategies/cash-secured-put 20. Managing Cash-Secured Puts for Income Strategies - Charles Schwab, https://www.schwab.com/learn/story/managing-cash-secured-equity-puts 21. Capital Gains and Losses - Writers of Calls and Puts - TaxAct, https://www.taxact.com/support/14604/capital-gains-and-losses-writers-of-calls-and-puts 22. Cost Basis Calculations for Assigned Put Options : r/fidelityinvestments - Reddit, https://www.reddit.com/r/fidelityinvestments/comments/1bdxhst/cost\_basis\_calculations\_for\_assigned\_put\_options/ 23. Options assignment & exercise \| Dallas TX \| www.optionstaxguy.com, https://www.optionstaxguy.com/assignment-exercise 24. What is a covered call? - Fidelity Investments, https://www.fidelity.com/learning-center/smart-money/covered-call 25. Wash-Sale Rule: How It Works & What to Know \| Charles Schwab, https://www.schwab.com/learn/story/primer-on-wash-sales 26. Wash Sales \| Investor.gov, https://www.investor.gov/introduction-investing/investing-basics/glossary/wash-sales 27. Wash-Sale Rules \| Avoid this tax pitfall - Fidelity Investments, https://www.fidelity.com/learning-center/personal-finance/wash-sales-rules-tax 28. Substantially Identical Security: Definition and Wash Sale Rules - Investopedia, https://www.investopedia.com/terms/s/substantiallyidenticalsecurity.asp 29. Wash Sale Rule - Examples, & Being Substantially Identical - Firstrade, https://www.firstrade.com/resources/tax-center/wash-sales 30. What is a Wash Sale? (Tax Rule for Trading) - Tastytrade Help Center, https://support.tastytrade.com/support/s/solutions/articles/43000435251 31. IRS broadens the definition of wash sales: can Cottage Savings carry the day?, http://archives.cpajournal.com/old/12826671.htm 32. How Taxing Is Your Options Trade? \| Cboe, https://www.cboe.com/insights/posts/how-taxing-is-your-options-trade/ 33. Form 1099-B: Cost Basis and Options Trading - Charles Schwab, https://www.schwab.com/learn/story/form-1099-b-cost-basis-and-options-trading 34. About Form 8949, Sales and other Dispositions of Capital Assets \| Internal Revenue Service, https://www.irs.gov/forms-pubs/about-form-8949 35. Instructions for Form 8949 - 2024 - IRS, https://www.irs.gov/pub/irs-pdf/i8949.pdf 36. Schedule D (Form 1040) - Capital Gains and Losses - TaxAct, https://www.taxact.com/support/601/schedule-d-form-1040-capital-gains-and-losses 37. Guide to Schedule D: Capital Gains and Losses - TurboTax Tax Tips & Videos - Intuit, https://turbotax.intuit.com/tax-tips/investments-and-taxes/guide-to-schedule-d-capital-gains-and-losses/L1bKWgPea 38. Video: When to Use IRS Form 8949 for Stock Sales - TurboTax Tax Tips & Videos - Intuit, https://turbotax.intuit.com/tax-tips/investments-and-taxes/video-when-to-use-irs-form-8949-for-stock-sales/L0rk0PeNa 39. What is Schedule D? \| Capital gains and losses - Fidelity Investments, https://www.fidelity.com/learning-center/smart-money/schedule-d 40. www.taxportalfaq.com, https://www.taxportalfaq.com/options\#:\~:text=Report%20it%20on%20Part%20I,consequences%20in%20the%20earlier%20year. 41. 2024 Instructions for Schedule D (2024) \| Internal Revenue Service, https://www.irs.gov/instructions/i1040sd 42. Topic no. 429, Traders in securities (information for Form 1040 or 1040-SR filers) - IRS, https://www.irs.gov/taxtopics/tc429
