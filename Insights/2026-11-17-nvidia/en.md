---
title: "NVIDIA Post-Jensen Huang: Moat Erosion, Capital Allocation Risks, and Intrinsic Value Implications"
date: "2026-11-17"
lang: "en"
category: "investing"
tickers: []
notebook_id: "5bc7662a-0655-47b5-87e4-e4c737deb027"
source_urls:
  - title: "“后黄仁勋时代”：英伟达的护城河、资本棋局与AI产业变数"
    url: "https://www.youtube.com/watch?v=xJUWVxZfNVI"
youtube:
  - title: "Nvidia Without Huang: The Case for a 25% Discount"
    url: "https://youtu.be/pBV1lc2jpw8"
    lang: "en"
    publish_at: "2026-11-21T18:00:00Z"
  - title: "輝達失去黃仁勳：估值至少打25%折扣？護城河還撐得住嗎"
    url: "https://youtu.be/bdymtmWNYJk"
    lang: "zh"
    publish_at: "2026-11-18T00:00:00Z"
podcast:
  - title: "NVIDIA (NVDA) — Nvidia Without Huang: The Case for a 25% Discount"
    url: "https://open.spotify.com/episode/0BscsOHLk3z1ibZ4oPjjW5"
    lang: "en"
  - title: "NVIDIA（NVDA）輝達失去黃仁勳：估值至少打25%折扣？護城河還撐得住嗎"
    url: "https://open.spotify.com/episode/0SSguIs7yUy2QtAzOcjSWH"
    lang: "zh"
generated_by: "NotebookLM + DeepValues editors"
disclosure: "AI-assisted"
---

# NVIDIA Post-Jensen Huang: Moat Erosion, Capital Allocation Risks, and Intrinsic Value Implications

This article evaluates NVIDIA Corporation's structural outlook, competitive positioning, and financial integrity following the abrupt resignation of founder and Chief Executive Officer Jensen Huang. Evaluating the semiconductor giant through a classic Benjamin Graham and Warren Buffett value-investing framework reveals that NVIDIA's historic CUDA software moat faces long-term compression from AI-driven code automation, its critical supply chain allocations from TSMC are highly vulnerable to competitive reallocation, and its aggressive balance sheet deployments into ecosystem equity introduce severe circular financing risks. For long-term value investors, the loss of key-person founder control—compounded by severe corporate governance flaws, an absence of dual-class voting control, and the departure of the company's primary enterprise relationship driver—justifies a substantial margin-of-safety discount on NVIDIA's equity valuation.

## Revenue Model and System-Level Shift: Beyond Single-GPU Dominance

NVIDIA’s fundamental business driver has shifted decisively away from selling standalone graphics processing unit (GPU) accelerator cards toward heterogeneous datacenter system integration. According to technical architecture evaluations detailed in *Silicon Valley 101*, modern artificial intelligence infrastructure requires deep vertical integration across computing hardware, software execution, and datacenter-scale physical design. NVIDIA generates revenue by delivering complex, system-level solutions that combine GPUs, central processing units (CPUs) such as the Grace Hopper architecture, high-speed networking stacks acquired through Mellanox, advanced liquid cooling technology, and specialized power delivery infrastructures, including 800-volt high-voltage transmission frameworks.

To manage system-level memory bottlenecks and work disaggregation, NVIDIA relies on an internal software suite for datacenter scheduling and compute optimization. As revealed in hardware analysis from *Silicon Valley 101*, this portfolio includes custom orchestration frameworks like DNamo, memory offloading architectures such as CPX to shift Key-Value (KV) cache directly to storage, and pre-fill and decode disaggregation technologies integrated through its acquisition of Groq.

Looking forward, NVIDIA’s hardware roadmap relies on advanced optical interconnects and highly complex heterogeneous chip combinations. As noted in recent industry disclosures, NVIDIA is developing Optical Circuit Switches (OCS) to replace proprietary NVLink switches—a strategic pivot toward optical topologies originally introduced by Google. Furthermore, NVIDIA’s next-generation Vera Rubin system architecture is engineered to integrate up to six distinct chip types into a single unified computing environment. 

Crucially, from a value-investing perspective, this technical transition serves as a defensive strategy against software moat decay. As CUDA's software-level lock-in compresses, NVIDIA is forced into capital-intensive, lower-margin hardware integration to maintain customer stickiness. Competitive differentiation in the semiconductor sector no longer rests on single-card raw compute performance, but rather on high-friction datacenter system execution.

## Durability of the Moat: CUDA Ecosystem Decay and TSMC Supply Chain Dependencies

Under the Warren Buffett value-investing framework, an economic moat must act as a structural barrier that protects return on invested capital over a multi-decade horizon. For nearly two decades, CUDA functioned as a classic Buffett "tollbooth" business model. Launched in 2006 as a parallel computing platform and programming model, CUDA allowed NVIDIA to collect an economic toll on all AI development. Even when competitors like AMD produced hardware with comparable price-to-performance metrics, customer switching costs remained prohibitive due to the specialized human engineering required to write custom software kernels and optimize execution frameworks.

However, automated AI coding agents are systematically lowering the height of this economic tollbooth. As revealed in a benchmark presentation disclosed by *Decoder* referencing research from Anthropic, porting AI workloads to alternative hardware platforms historically required 6 to 12 months of manual development by dozens of specialized engineers. Using modern AI coding agents, an engineering team adapted a specific prompt-processing inference task for an AI model onto an AMD MI350X GPU in approximately 3 days. While this specific benchmark was demonstrated for a prompt-processing inference task and does not immediately equate to a full-system, cross-platform application migration, it demonstrates a structural shift. AI agents compile high-level application code directly into low-level machine assembly instructions, bypassing intermediate CUDA runtime layers entirely and eliminating human kernel-writing bottlenecks.

Simultaneously, NVIDIA’s supply chain architecture presents extreme counterparty concentration risk. In a March interview with Lex Fridman, Jensen Huang acknowledged the unusual nature of NVIDIA’s core manufacturing dependency, stating: "Decades, I don't know how many tens, hundreds of billions of dollars business we done through them, and we don't have a contract."

According to *TSMC's 2025 annual financial report*, NVIDIA became TSMC’s largest single customer, generating 19% of TSMC's total annual revenue. Furthermore, industry research firm estimates cited in *Silicon Valley 101* indicate that NVIDIA consumed approximately 60% of global Chip-on-Wafer-on-Substrate (CoWoS) advanced packaging capacity in 2025. TSMC historically prioritized NVIDIA’s massive advanced packaging demand based on mutual trust established personally by Huang, who offered TSMC multi-year demand visibility to justify capital-intensive fabrication expansion.

Without Huang leading executive operations, TSMC faces strong commercial incentives to diversify its wafer and CoWoS packaging allocations. To mitigate customer concentration risk, TSMC is incentivized to allocate advanced node capacity to competitors like AMD, whose open-source ROCm software ecosystem continues to gain enterprise traction. Any reallocation of advanced packaging capacity directly limits NVIDIA's shipping capability and compresses its revenue ceiling.

## Management, Governance, and Capital Allocation: Founder Centralization and Circular Financing

An evaluation of NVIDIA’s corporate governance under classic Benjamin Graham principles highlights severe key-person concentration risks, capital allocation vulnerabilities, and balance sheet exposures.

NVIDIA operated under an extreme "Founder's Mode" organizational structure. As reported by *Silicon Valley 101*, over 60 senior executives reported directly to Huang without intermediate business unit heads or operational layers. Strategic execution across engineering, sales, and supply chain management depended on Huang’s personal oversight. Beyond internal operations, Huang functioned as NVIDIA's primary enterprise salesperson. He personally hand-delivered the first DGX-1 supercomputer to OpenAI in 2016, negotiated directly with executives like Larry Ellison and Elon Musk, and brokered multi-gigawatt sovereign AI infrastructure deals with foreign governments. This irreplaceable enterprise sales dynamic represented an unquantified personal relationship moat that cannot simply be transferred to a successor.

Despite his central operational role, Huang maintained an equity ownership stake of just 3.58% in NVIDIA. Crucially, when NVIDIA completed its initial public offering in 1999, the company did not establish a dual-class (A/B) voting stock structure. Consequently, Huang lacked super-voting rights, leaving him vulnerable to rapid board dismissal during corporate governance disputes.

Following Huang's departure, severe questions emerge regarding NVIDIA’s capital allocation practices. To stimulate demand for its high-end systems, NVIDIA aggressively deployed cash reserves into downstream software labs, model developers, and datacenter infrastructure builders. Financial records show that by July 2026, NVIDIA had spent $42.4 billion in cumulative cash purchasing equity in external enterprises. By late July 2026, the valuation of NVIDIA’s held equity portfolio reached $99.0 billion, with the company carrying $25.0 billion in additional committed capital for follow-on investments.

From a Graham and Dodd perspective, this strategy introduces circular financing risks that obscure true cash flow quality. NVIDIA routinely purchased equity in emerging "NeoLabs"—such as Thinking Machines Lab, founded in March by former OpenAI Chief Technology Officer Mira Murati, which planned to deploy at least 1 gigawatt (GW) of NVIDIA Vera Rubin systems. In these structures, NVIDIA commits capital to model builders, who use those funds to purchase cloud compute capacity from cloud service providers, who subsequently purchase GPUs from NVIDIA. Strategic equity investments made without strict financial return hurdles create circular revenue recognition loops that artificially inflate AI startup valuations and mask underlying end-user demand.

This aggressive balance sheet posture created severe friction within NVIDIA's executive leadership. According to governance coverage by *The Information* and executive management reports from the *Wall Street Journal*, a rift emerged between Huang and Chief Financial Officer Colette Kress (appointed interim CEO following Huang's exit). Kress repeatedly objected to high-risk balance sheet guarantees, including a proposed $250 billion debt financing guarantee to support OpenAI’s datacenter expansion. Kress intervened directly, restructuring the transaction to cut NVIDIA’s initial phase financing guarantee by more than half. Internal reporting reveals that during an executive meeting regarding these debt guarantees, Huang berated Kress, publicly comparing her hesitant response to a "deer caught in headlights" ("像隻被車頭燈照傻的鹿"). This public clash highlighted a fundamental conflict between founder-led revenue inflation and disciplined capital preservation.

## Owner Earnings, Human Capital, and Intrinsic Value Assessment

Evaluating NVIDIA's intrinsic value requires discounting future owner earnings against key-person loss and human capital retention headwinds. Following Huang's departure, market consensus estimates compiled by *Silicon Valley 101* indicate that institutional investors apply at least a 25% valuation discount to NVIDIA's equity narrative to account for the loss of his key-person leadership, sales execution, and supply chain influence.

Human capital retention poses an immediate threat to operational execution. NVIDIA’s equity price appreciation (~1,400% from late 2022 to September) generated substantial wealth across its senior technical staff. Based on compensation estimations from *Levels.fyi*, a senior software engineer who joined NVIDIA in 2022 held stock valued at approximately $4.1 million by late 2024. This level of wealth accumulation has accelerated voluntary engineer departures, early retirements, and exits to early-stage startups.

Conversely, NVIDIA's recruitment leverage for new talent has weakened. Equity compensation packages granted at historically elevated valuation multiples offer diminished upside relative to competing private AI laboratories like OpenAI or Anthropic. 

Prior to Huang's exit, NVIDIA attempted to consolidate distribution channels by acquiring developer hubs. In early September, Huang announced the acquisition of Hugging Face, the dominant open-source AI platform. As reported by *Silicon Valley 101* and confirmed by *Leonos Capital* partner JNY, Hugging Face maintained a massive ecosystem footprint prior to the announcement, comprising over 20 million registered users, 200,000 corporate accounts, 3.23 million hosted models, 1.13 million datasets, and over 1.4 million applications. However, this acquisition faces active antitrust investigations by the United States Department of Justice (DOJ), leaving NVIDIA's distribution control strategy uncertain.

Without founder-led sales execution, facing structural margin compression as customers transition toward complex system architectures, and operating under regulatory scrutiny, NVIDIA’s equity valuation lacks an adequate Graham-style margin of safety.

## Key numbers

* **19%**: NVIDIA's contribution to TSMC's total annual revenue, according to TSMC's 2025 annual financial report.
* **~60%**: Share of global CoWoS advanced packaging capacity consumed by NVIDIA in 2025, based on industry research firm estimates.
* **3 days**: Time required by an AI coding agent to adapt an AI inference task onto an AMD GPU, down from 6–12 months and dozens of engineers (Decoder benchmark report).
* **$42.4 billion**: Cumulative cash spent by NVIDIA to purchase equity stakes in external companies as of July 2026.
* **$99.0 billion**: Total valuation of NVIDIA's held equity investment portfolio at the end of July 2026.
* **$25.0 billion**: NVIDIA's committed cash for follow-on equity investments as of mid-2026.
* **3.58%**: Jensen Huang’s equity ownership stake in NVIDIA at the time of his departure.
* **At least 25%**: Market consensus valuation discount applied to NVIDIA's enterprise narrative following Huang's exit.
* **~1,400%**: NVIDIA stock price appreciation percentage from late 2022 to September.
* **$4.1 million**: Estimated equity holdings value for a senior software engineer hired at NVIDIA in 2022, based on Levels.fyi data.
* **20 million users / 200,000 companies / 3.23 million models**: Footprint metrics of Hugging Face prior to its early September acquisition announcement.
* **Over 60**: Number of direct executive reports to Jensen Huang under NVIDIA’s flat managerial model.

## What would change our view

* Formalization of binding, multi-year capacity reservation contracts between TSMC, NVIDIA, and major competitors, ensuring long-term CoWoS advanced packaging allocation stability regardless of executive turnover.
* Broad commercial enterprise adoption of alternative open-source software stacks (such as AMD's ROCm ecosystem), demonstrated by verified large-scale multi-cloud migration away from proprietary CUDA software layers.
* Formal regulatory clearance or unconditional termination of United States Department of Justice (DOJ) antitrust investigations regarding the Hugging Face acquisition and software distribution channels.
* Structural reform or complete termination of strategic balance sheet equity investments in NeoLabs, eliminating circular financing structures in favor of conservative cash preservation and transparent financial reporting.

## Our stance

Bearish. NVIDIA faces simultaneous structural compression across its proprietary software moat, supply chain allocation privileges, and corporate governance structure following the abrupt removal of its founder CEO. The combination of AI coding agents degrading CUDA switching costs, internal executive friction over high-risk circular equity investments, and the loss of its primary enterprise sales driver without voting control protections severely compromises NVIDIA's long-term risk-reward profile. To analyze more open-source semiconductor research or evaluate your portfolio’s intrinsic value margin of safety, explore the tools available in the DeepValues app.

## Sources

Video Transcript: "“后黄仁勋时代”：英伟达的护城河、资本棋局与AI产业变数", Silicon Valley 101 (硅谷101)  
TSMC 2025 Annual Financial Report  
Lex Fridman Podcast Interview with Jensen Huang  
The Information Corporate Governance Report  
Wall Street Journal Executive Management Report  
Decoder Technical PPT Presentation & Benchmark Report  
Levels.fyi Compensation Estimations Data
