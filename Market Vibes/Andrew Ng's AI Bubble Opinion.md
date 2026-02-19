# The Structural Dynamics of Artificial Intelligence Valuation: A Comprehensive Analysis of Andrew Ng's Tripartite Market Thesis

## Executive Summary

The global technology market currently stands at a precarious inflection point, characterized by a rapid and unprecedented accumulation of capital within the artificial intelligence (AI) sector. With aggregate valuations of semiconductor manufacturers and foundation model providers briefly approaching or exceeding the GDP of major industrial nations, the discourse surrounding a potential "AI Bubble" has moved from fringe skepticism to central banking critique. Into this volatile narrative enters Dr. Andrew Ng, a seminal figure in the development of deep learning, whose analysis in late 2025 provides a stabilizing, albeit complex, framework for understanding these market dynamics.

This report offers an exhaustive deconstruction of Ng's thesis as presented in *The Batch* (Issue 329) and supported by his extensive commentary throughout 2024 and 2025. Unlike the binary reductionism that dominates cable financial news-which seeks to label the entire AI phenomenon as either a "boom" or a "bubble"-Ng proposes a stratified economic model. His "Tripartite Stack" theory posits that the AI market is not a monolith but a composite of three distinct economic layers: **Training Infrastructure**, **Inference Infrastructure**, and the **Application Layer**.

Through a rigorous examination of recent data, historical parallels to the Dot-com era, and technical analysis of "agentic" workflows, this report validates Ng's core assertion: that while the capital-intensive infrastructure layers exhibit signs of speculative overheating, the application layer remains structurally undercapitalized relative to its latent economic utility. This "Valuation Inversion" represents both the primary risk and the primary opportunity in the current cycle. The stabilization of the AI economy, according to this analysis, depends entirely on the rapid maturation of agentic workflows-autonomous software systems that can translate raw compute into tangible labor substitution-thereby generating the revenue necessary to service the massive debts incurred by infrastructure build-outs.

## 1. Macro-Economic Context and the Monolithic Fallacy

### 1.1 The Landscape of Hyper-Capitalization

To understand the gravity of Andrew Ng's analysis, one must first appreciate the magnitude of the capital flows defining the 2025 AI landscape. The market has witnessed the proposal of infrastructure projects valued at over $1.4 trillion, with single entities like Nvidia briefly surpassing $5 trillion in market capitalization.<sup>1</sup> These figures are not merely large; they represent a fundamental reallocation of global capital expenditure (CapEx) away from traditional industrial sectors and into the construction of data centers and silicon fabrication capacity.

The prevailing anxiety, articulated by institutions such as Janus Henderson and various economic forums, is that this spending is predicated on speculative future demand rather than current revenue realities.<sup>3</sup> Skeptics argue that the "revenue gap"-the difference between the money spent on chips and the money earned from AI software-is unsustainable. If the anticipated demand for AI services fails to materialize at a scale commensurate with the infrastructure build-out, the resulting correction could trigger a deflationary shock across the broader technology sector.

### 1.2 Ng's Rejection of the Monolith

Andrew Ng's intervention in *The Batch* Issue 329 challenges the fundamental premise of the "AI Bubble" question. He argues that asking "Is there an AI bubble?" is analytically flawed because it treats AI as a monolithic asset class. This monolithic view obscures the divergent economic physics governing different parts of the technology stack.<sup>2</sup>

Ng's framework disaggregates the industry into three functional layers, each with its own risk profile, capital requirements, and competitive dynamics:

1.  **The Application Layer:** The interface between the technology and the end-user (e.g., automated legal review, medical diagnosis systems, coding agents).

2.  **Inference Infrastructure:** The computational resources required to *execute* models for end-users (the "runtime" environment).

3.  **Training Infrastructure:** The massive, burst-oriented computational resources required to *create* and *train* foundation models (the "factory" environment).<sup>2</sup>

This segmentation is crucial because it aligns with historical technological diffusions. In the electrification of the early 20th century-a metaphor Ng frequently employs <sup>4</sup>-there were distinct bubbles in copper mining (infrastructure) and utility holding companies (distribution), which operated independently of the eventual value created by electrical appliances (applications). Ng posits that we are currently seeing a similar decoupling, where the "Training" layer may be overheating while the "Application" layer is largely ignored by capital allocators.<sup>2</sup>

## 2. The Training Infrastructure Bubble: A Crisis of Depreciating Assets

### 2.1 The Economics of Excess

The most provocative element of Ng's 2025 analysis is his admission that the **Training Infrastructure** sector may indeed be in a bubble. He states, "I'm still cautiously optimistic about this sector, but there could also be a bubble".<sup>2</sup> This caution stands in stark contrast to the unbridled enthusiasm of hardware manufacturers and cloud hyperscalers.

The economic logic underpinning this risk assessment is multifaceted. Training foundation models is an inherently capital-intensive process that requires the aggregation of hundreds of thousands of high-performance Graphical Processing Units (GPUs) into singular clusters. However, the value of this infrastructure is precarious due to the pace of technological obsolescence.

#### 2.1.1 The Depreciation Trap

Unlike real estate or traditional industrial machinery, which depreciates over decades, AI training hardware is subject to "Moore's Law" dynamics. A GPU cluster purchased for $1 billion in 2023 is likely to be outperformed by a $500 million cluster in 2026 due to architectural advancements (e.g., the shift from Hopper to Blackwell architectures).

Ng's caution reflects the understanding that data center assets act as "fast-depreciating assets" with "minimal cash flow to show for them" during the training phase.<sup>5</sup> If a company invests billions to train a model that fails to achieve state-of-the-art (SOTA) performance-or if the SOTA benchmark moves before the model is deployed-that capital is effectively incinerated. The hardware retains some residual value for inference, but nowhere near the premium paid for training capabilities.

#### 2.1.2 The "Foundation Model Race" Saturation

The "Training Bubble" is further exacerbated by the redundancy of effort. Currently, dozens of entities-including OpenAI, Google, Anthropic, Meta, xAI, and various sovereign wealth funds-are building overlapping infrastructure to train competing general-purpose Large Language Models (LLMs). Ng's analysis implies that the market cannot support dozens of proprietary foundation models.<sup>6</sup>

As open-source models (like Meta's Llama series) continue to close the performance gap with proprietary models, the pricing power of closed models erodes. If the marginal cost of intelligence trends toward zero due to open-source competition, the massive CapEx investments made by proprietary model builders may never yield the expected returns. This creates a classic "overinvestment cycle" typical of bubbles, where too many competitors spend too much capital chasing a finite profit pool.

### 2.2 Financial Engineering and Circular Risks

Deepening the risk profile of the training layer is the phenomenon of "financing complexity" and "circular references" highlighted in broader market analyses congruent with Ng's views.<sup>3</sup> Major cloud providers (hyperscalers) are investing billions into AI startups (like OpenAI or Anthropic) primarily in the form of "cloud credits."

-   **Mechanism:** Company A (Cloud Provider) invests $10 billion in Company B (Model Builder). Company B is contractually obligated to spend that $10 billion on Company A's compute services.

-   **Result:** Company A books the investment as an asset and the subsequent cloud usage as revenue.

This circularity inflates the apparent demand for training infrastructure. It creates a "vendor financing" dynamic reminiscent of the telecom bubble, where demand is synthetic rather than organic. While Ng does not explicitly dissect corporate balance sheets in *The Batch*, his identification of the training layer as the locus of bubble risk <sup>2</sup> aligns with the danger posed by these artificial revenue loops. If the underlying startups fail to generate real revenue from applications, the "cloud revenue" booked by the hyperscalers will evaporate, revealing the training infrastructure as a stranded asset.<sup>5</sup>

## 3. The Inference Imperative: The Undervalued Workhorse

### 3.1 Differentiating Compute Workloads

A critical distinction in Ng's thesis is the separation of **Training** from **Inference**. While training is the process of teaching the model (akin to a student studying for years), inference is the process of the model working (the graduate performing a job).

Ng asserts that **Inference Infrastructure** "still needs significant investment".<sup>2</sup> This is a counter-intuitive finding for those who view "chips" as a single category. The market may be oversupplied with the massive, networked clusters needed for training, yet undersupplied with the efficient, low-latency chips needed for serving millions of users.

### 3.2 The Utilization Gap

The bullish case for inference infrastructure relies on the eventual success of the application layer. If AI applications scale as Ng predicts, the demand for inference compute will grow exponentially, potentially dwarfing the demand for training compute.

-   **Training Demand:** Periodic, bursty, consolidated among a few dozen players.

-   **Inference Demand:** Continuous, real-time, distributed among millions of enterprises and billions of users.

However, a risk remains. If the application layer fails to materialize, the inference capacity will also sit idle. The current "underinvestment" in inference is only a problem if there are successful applications that need to be run. Thus, Ng's call for more inference investment is implicitly a bet on the success of the application layer.<sup>2</sup>

### 3.3 The Shift in Capital Intensity

Inference infrastructure generally requires different technical specifications than training. While training requires massive interconnect bandwidth (e.g., NVLink) to synchronize thousands of GPUs, inference can often be run on smaller, isolated clusters or even edge devices. This suggests a future democratization of infrastructure, moving away from the "Winner-Take-All" dynamics of the training layer toward a more competitive, commodity-like market for inference hosting. This aligns with Ng's broader philosophy of AI democratization and the "green shoots" of diverse applications.<sup>2</sup>

## 4. The Application Layer: The Locus of Value and the "Green Shoots"

### 4.1 The Underinvestment Paradox

The most significant insight in Ng's analysis is the identification of a massive inefficiency in capital allocation: the **Application Layer** is severely underinvested.<sup>2</sup>

Despite the media hype, Ng observes that venture capital has been hesitant to deploy funds into pure-play AI applications. This hesitancy stems from a "fear of the giants"-investors worry that any application (e.g., a PDF summarizer) will be rendered obsolete by the next update of a foundation model (e.g., GPT-5 including native PDF summarization). This phenomenon, known as "Sherlocking" in the Apple ecosystem, has paralyzed investment in the application layer.

Ng argues that this fear is misplaced and grounded in a misunderstanding of value creation. He notes, "The potential is still much greater than most realize".<sup>2</sup> The "recipe" for building infrastructure ($1B for chips + power) is simple and understood by finance professionals. The "recipe" for building a successful AI application (domain expertise + workflow integration + user trust) is complex, messy, and vertical-specific, making it harder for generalist investors to evaluate.<sup>2</sup>

### 4.2 The Mathematical Necessity of Applications

Ng presents a fundamental economic truism: The value of the stack must exceed the cost of the foundation.

"Almost by definition, applications that are built on top of AI infrastructure/technology (such as LLM APIs) have to be more valuable than the infrastructure, since we need them to be able to pay the infrastructure and technology providers".2

This simple equation drives the entire "Bubble" thesis.

-   *Scenario A (Bubble Bursts):* Total Revenue of Apps &lt; Total Cost of Infrastructure.

-   *Scenario B (Sustainable Growth):* Total Revenue of Apps &gt; Total Cost of Infrastructure.

Currently, the market is in Scenario A. The infrastructure is being subsidized by VC cash and corporate balance sheets. To move to Scenario B, the application layer must explode in value. Ng sees "green shoots"-early signs of success-that give him confidence this transition will occur.<sup>2</sup>

### 4.3 Vertical Integration and Defensibility

To survive the "Sherlocking" risk, Ng advocates for deep vertical integration. A generic "writing assistant" is vulnerable. A "regulatory compliance agent for FDA filings in the pharmaceutical industry" is defensible. The latter requires deep domain knowledge, proprietary data, and integration into legacy enterprise systems-moats that a generic foundation model cannot easily cross.

Ng points to the "Developer Tooling Layer" as a battleground, but the "Application Layer" as the land of opportunity with "relatively less competition" because everyone is focused on the lower layers.<sup>4</sup> This implies that the smartest capital should be moving *up* the stack, away from the commoditized models and into the complex workflows.

## 5. The Agentic Transformation: The Mechanism of ROI

### 5.1 Redefining the Unit of Work

If the application layer is the savior of the AI economy, **Agentic Workflows** are the specific technology that will enable it. Ng has been a vocal proponent of the shift from "Chatbots" to "Agents" throughout late 2024 and 2025.<sup>7</sup>

-   **Chatbot (The Old Paradigm):** A system that retrieves information or generates text based on a prompt. It is a productivity *aid*.

-   **Agent (The New Paradigm):** A system that can plan, iterate, use tools, and execute complex multi-step workflows to achieve a broad goal. It is a labor *substitute*.<sup>9</sup>

Ng emphasizes that the "PR hype" is often focused on model size (which is hitting diminishing returns), while the "business reality" is focused on agentic capabilities (which are just beginning to scale).<sup>8</sup>

### 5.2 The Iterative Cycle of Agents

Ng describes agentic workflows as having four key characteristics that drive superior performance:

1.  **Reflection:** The agent critiques its own output (e.g., "Does this code compile? No. Why?").

2.  **Tool Use:** The agent accesses external APIs, databases, or browsers.

3.  **Planning:** The agent breaks a high-level goal ("Build a website") into sub-tasks.

4.  **Multi-agent Collaboration:** Different agents with different "personas" (coder, reviewer, designer) work together.<sup>9</sup>

This shift is critical for the "Bubble" discussion because agents unlock a much larger Total Addressable Market (TAM). A chatbot competes with a Google search (low value). An agent competes with a junior developer or a paralegal (high value). If AI can reliably perform the work of an entry-level employee, the revenue potential skyrockets, justifying the massive infrastructure costs.

### 5.3 The Coding Example and "Green Shoots"

Ng frequently cites coding agents as a prime example of this shift.<sup>7</sup> A developer using a chatbot might code 20% faster. A developer managing a "swarm" of coding agents might be 500% more productive, or simply act as a reviewer for autonomous code generation.

He argues that we are seeing "green shoots" in sectors like legal analysis and document processing, where agents are beginning to perform tasks that require "nuanced understanding" rather than just keyword matching.<sup>2</sup> These applications are the "forest" that needs to grow to support the "climate" of the infrastructure layer.

## 6. Historical Comparative Analysis: The Dot-Com Mirror

### 6.1 Structural Parallels and Divergences

Andrew Ng and the surrounding discourse frequently utilize the 2000 Dot-com crash as a heuristic device to evaluate the current AI market. While there are similarities, Ng's analysis suggests crucial structural differences.<sup>3</sup>

**Table 1: Comparative Analysis of Dot-Com Bubble (2000) vs. AI Surge (2025)**

| **Feature**                | **Dot-Com Era (2000)**                   | **AI Era (2025)**                                        | **Ng's Assessment**                                                                                      |
|----------------------------|------------------------------------------|----------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| **Primary Capital Source** | Speculative IPOs, Retail Investors       | Corporate Balance Sheets (Big Tech), Sovereign Wealth    | **More Stable:** The current boom is funded by profitable giants, not unprofitable startups.<sup>3</sup> |
| **Infrastructure State**   | "Dark Fiber" glut (unused capacity)      | GPU Shortage (constrained capacity)                      | **Risk of Glut:** Training infra could become the "dark fiber" of 2026 if apps don't scale.<sup>5</sup>  |
| **Profitability**          | Negative Margins (Netscape, Pets.com)    | Record Margins (Microsoft, Meta, Google)                 | **Higher Quality:** The key players have massive cash reserves to weather a downturn.<sup>13</sup>       |
| **Technology Utility**     | Low (Dial-up speeds, nascent web)        | High (Production-grade code generation, medical imaging) | **Real Utility:** AI is already "deeply integrated," unlike the speculative web of 1999.<sup>13</sup>    |
| **Valuation Metrics**      | "Eyeballs" (User growth without revenue) | Price-to-Earnings (High, but earnings exist)             | **More Rational:** Though high, valuations are tethered to actual cloud revenue growth.                  |

### 6.2 The "Build It and They Will Come" Fallacy

In the late 1990s, telecom companies spent billions laying fiber optic cables, anticipating exponential traffic growth. When that growth arrived slower than expected, the companies went bankrupt (e.g., Global Crossing), even though the fiber was eventually used.

Ng's warning about the **Training Infrastructure Bubble** mirrors this.<sup>2</sup> If companies build data centers for a level of AI demand that is 5 years away, but debt service is due next year, they will face a solvency crisis. The physical assets (GPUs) are even riskier than fiber because fiber lasts 20 years, whereas GPUs are obsolete in 3.<sup>5</sup> This "asset-liability mismatch" is the specific mechanism of the potential crash.

### 6.3 The "Napster" Moment

While not explicitly quoting "Napster" in the provided text, the cultural reference in Ng's broader educational content often relates to the "installation phase" vs. the "deployment phase" of technology. The Dot-com crash destroyed the investors, but it installed the internet. Similarly, an AI crash might destroy the GPU investors, but it would leave behind the infrastructure and models that transform society. Ng focuses on the long-term utility ("AI is the new electricity") regardless of the short-term financial volatility.<sup>4</sup>

## 7. Geopolitical and Educational Dimensions

### 7.1 The Global AI Race

The "Bubble" is not merely a market phenomenon; it is a geopolitical one. Ng discusses the varying approaches of the US, China, and Europe.<sup>7</sup>

-   **China:** Facing export controls, China is investing heavily in domestic chip infrastructure. This creates a parallel market that distorts global demand figures.

-   **US vs. Open Source:** The US policy debate around "closing" models versus supporting open source affects the "Training" layer's profitability. If the US government supports open source to maintain global influence, it undermines the business model of proprietary labs, further deflating the "Training Bubble" while boosting the "Application Layer" (which benefits from free models).

### 7.2 The Skills Gap as a Market Brake

A critical bottleneck identified by Ng is the shortage of human capital. The "Application Layer" cannot grow if there are no engineers to build it.

"Just as human work is complicated... it's taking everyone a while to look at the very complex workflows and to build AI agentic workflows".8

This skills gap acts as a governor on the market. It slows down the "green shoots," potentially causing the "Infrastructure Layer" to overheat before the demand arrives. Ng's massive investment in education (Coursera, DeepLearning.AI) is a strategic attempt to widen this bottleneck. He argues that we must teach "coding" and "agentic orchestration" to the next generation to ensure the economic promise of AI is realized.<sup>7</sup>

## 8. Strategic Risk Assessment: The Data Center Precipice

### 8.1 The Asset Class Identity Crisis

A nuanced risk highlighted in the research material is the identity crisis of data centers. Are they **Real Estate** or **Infrastructure**?

-   **Real Estate:** Passive assets with long-term tenants.

-   **Infrastructure:** Active assets with operational risk.

Snippet <sup>5</sup> argues they are hybrid assets with "tenant churn risks" and "fast-depreciating assets." In a bubble scenario, if AI startups go bust, they default on their cloud contracts. The data center owner is left with a building full of obsolete H100s that consume massive amounts of power but generate no revenue. This "counterparty risk" is systemic. If a major model builder fails, the shockwave hits the cloud provider, the chip manufacturer, and the energy utility.

### 8.2 Energy and Environmental Constraints

Ng also notes the physical constraints-energy bottlenecks.<sup>11</sup> The "Bubble" might not pop due to finance, but due to physics. If data centers cannot get power, the growth stops. This creates a "scarcity bubble" where existing powered racks become incredibly valuable, while unpowered chips become worthless.

## 9. Conclusion: The "Soft Landing" Scenario

### 9.1 Synthesis of Ng's Outlook

Andrew Ng's answer to "Is there an AI bubble?" is a sophisticated "Yes and No."

-   **Yes,** in the **Training Infrastructure** layer, where capital is chasing redundant model creation and facing rapid depreciation risks.<sup>2</sup>

-   **No,** in the **Application Layer**, which is fundamentally undercapitalized and holds the key to future value.<sup>2</sup>

-   **Maybe,** in the **Inference Layer**, which is underbuilt but dependent on the success of apps.

### 9.2 The Path Forward

For the AI economy to achieve a "soft landing" (avoiding a 2000-style crash), capital must rotate efficiently.

1.  **Stop** funding the 50th foundation model.

2.  **Start** funding the 5,000th agentic workflow.

3.  **Bridge** the gap with education and tooling.

Ng remains an optimist because he sees the *utility* of the technology as genuine. Unlike the "Pet Rocks" of the Dot-com era, AI agents can actually write code, diagnose diseases, and optimize supply chains. The "Value Gap" will eventually close, provided the market creates enough useful applications before the debt on the infrastructure comes due.

### 9.3 Final Recommendation for Observers

Observers should shift their gaze from the "Model Leaderboards" (who has the smartest chatbot?) to the "ROI Leaderboards" (who is saving money with agents?). The burst of the "Training Bubble" may be inevitable and even healthy, as it will consolidate the market and lower costs for the "Application Layer," triggering the true Golden Age of AI deployment. As Ng concludes, "The potential is still much greater than most realize".<sup>2</sup>

### Data Appendix: Key Indicators Watchlist

| **Indicator**         | **Bubble Signal (Danger)** | **Sustainable Signal (Ng's View)** |
|-----------------------|----------------------------|------------------------------------|
| **GPU Utilization**   | Low (Hoarding chips)       | High (Inference usage)             |
| **App Layer Funding** | Low (VC fear)              | Rising (Green shoots)              |
| **Model Pricing**     | Crashing (Race to zero)    | Stable (Value-based)               |
| **Corporate Margins** | Declining (High CapEx)     | Improving (AI efficiencies)        |
| **Agent Adoption**    | "Toy" demos                | Production deployment              |

### Referenced Sources

-   <sup>2</sup> - *The Batch* Issue 329 (Ng's core thesis).

-   <sup>1</sup> - *The Batch* Letters (Market Cap context).

-   <sup>2</sup> - Ng's interviews on Coding/Agents/Geopolitics.

-   <sup>8</sup> - Ng on Hype vs. Reality.

-   <sup>3</sup> - Dot-com comparative data.

-   <sup>5</sup> - Infrastructure and Data Center financial risks.

-   <sup>4</sup> - AI Stack analysis.

-   <sup>9</sup> - Agentic Workflows.

#### Works cited

1.  Letters from Andrew Ng \| The Batch - DeepLearning.AI, accessed November 28, 2025, [<u>https://www.deeplearning.ai/the-batch/tag/letters/</u>](https://www.deeplearning.ai/the-batch/tag/letters/)

2.  Google Rules Arena Leaderboards, Microsoft+Anthropic, Record Labels Back AI Music, and more... - DeepLearning.AI, accessed November 28, 2025, [<u>https://www.deeplearning.ai/the-batch/issue-329/</u>](https://www.deeplearning.ai/the-batch/issue-329/)

3.  AI versus the Dotcom Bubble: 8 reasons the AI wave is different - Janus Henderson, accessed November 28, 2025, [<u>https://www.janushenderson.com/en-gb/investor/article/ai-versus-the-dotcom-bubble-8-reasons-the-ai-wave-is-different/</u>](https://www.janushenderson.com/en-gb/investor/article/ai-versus-the-dotcom-bubble-8-reasons-the-ai-wave-is-different/)

4.  "AI is the New Electricity": Insights from Dr. Andrew Ng - UC Berkeley Sutardja Center, accessed November 28, 2025, [<u>https://scet.berkeley.edu/ai-is-the-new-electricity-insights-from-dr-andrew-ng/</u>](https://scet.berkeley.edu/ai-is-the-new-electricity-insights-from-dr-andrew-ng/)

5.  Bubble or Nothing: Data Center Project Finance, accessed November 28, 2025, [<u>https://publicenterprise.org/wp-content/uploads/Bubble-or-Nothing.pdf</u>](https://publicenterprise.org/wp-content/uploads/Bubble-or-Nothing.pdf)

6.  Layers of the AI Stack, Explained Simply \| Towards Data Science, accessed November 28, 2025, [<u>https://towardsdatascience.com/layers-ai-stack/</u>](https://towardsdatascience.com/layers-ai-stack/)

7.  Andrew Ng on America's standing in the AI race (with DJ Patil) \| Masters of Scale Summit 2025 - YouTube, accessed November 28, 2025, [<u>https://www.youtube.com/watch?v=XeUAu65unu8</u>](https://www.youtube.com/watch?v=XeUAu65unu8)

8.  Andrew Ng warns AI hype is distorting its true value - FastForward, accessed November 28, 2025, [<u>https://fastforward.boldstart.vc/andrew-ng-warns-ai-hype-is-distorting-its-true-value/</u>](https://fastforward.boldstart.vc/andrew-ng-warns-ai-hype-is-distorting-its-true-value/)

9.  Focus on AI applications, not just workflows: Andrew Ng's keynote at ScaleUp:AI '24, accessed November 28, 2025, [<u>https://www.insightpartners.com/ideas/focus-on-ai-applications-not-just-on-workflows-andrew-ngs-keynote-at-scaleupai-24/</u>](https://www.insightpartners.com/ideas/focus-on-ai-applications-not-just-on-workflows-andrew-ngs-keynote-at-scaleupai-24/)

10. The AI Bubble, explained - The Neuron, accessed November 28, 2025, [<u>https://www.theneurondaily.com/p/the-ai-bubble-explained</u>](https://www.theneurondaily.com/p/the-ai-bubble-explained)

11. The Batch \| DeepLearning.AI \| AI News & Insights, accessed November 28, 2025, [<u>https://www.deeplearning.ai/the-batch/</u>](https://www.deeplearning.ai/the-batch/)

12. Rule 11 Is No Match for Generative AI - Stanford Law School, accessed November 28, 2025, [<u>https://law.stanford.edu/wp-content/uploads/2024/07/Rule-11-and-Gen-AI\_Publication\_Version.pdf</u>](https://law.stanford.edu/wp-content/uploads/2024/07/Rule-11-and-Gen-AI_Publication_Version.pdf)

13. AI Bubble vs. Dot-com Bubble: A Data-Driven Comparison \| IntuitionLabs, accessed November 28, 2025, [<u>https://intuitionlabs.ai/articles/ai-bubble-vs-dot-com-comparison</u>](https://intuitionlabs.ai/articles/ai-bubble-vs-dot-com-comparison)

14. AI Hype vs. Dot-Com Bubble: A 25-Year Market Lens - CKGSB, accessed November 28, 2025, [<u>https://english.ckgsb.edu.cn/knowledge/professor\_analysis/dot-com-to-deepseek-25-year-tech-bubble-comparison-for-ai-er/</u>](https://english.ckgsb.edu.cn/knowledge/professor_analysis/dot-com-to-deepseek-25-year-tech-bubble-comparison-for-ai-er/)
