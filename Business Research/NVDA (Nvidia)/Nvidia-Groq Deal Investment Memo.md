# INVESTMENT MEMORANDUM: Project Velocity — NVIDIA’s Strategic Consolidation of the Inference Market

Date: December 27, 2025

Subject: Strategic Analysis of NVIDIA’s $20 Billion Licensing & Talent Acquisition of Groq

Ticker: NASDAQ: NVDA

Target: Groq Inc. (Asset License & Human Capital)

Transaction Value: \~$20 Billion (All-Cash)

Deal Status: Definitive Agreement Signed; Regulatory Review Pending

## Executive Summary

On December 24, 2025, NVIDIA Corporation (NASDAQ: NVDA) announced a definitive agreement to secure the core intellectual property and engineering talent of AI hardware pioneer Groq in a transaction valued at approximately $20 billion.<sup>1</sup> This deal, structured uniquely as a "non-exclusive licensing and reverse acqui-hire" agreement rather than a traditional equity merger, represents the most significant strategic maneuver in the semiconductor industry since the failed acquisition of ARM Holdings.<sup>3</sup>

The transaction occurs at a critical inflection point in the artificial intelligence market, a phenomenon we classify as the "Inference Flip." For the past decade, the primary value driver in AI has been *training*—the computationally intensive process of creating models—where NVIDIA’s GPU architecture holds a near-monopoly. However, late 2025 marked the crossover point where global revenue from *inference*—the deployment of models for real-time interaction—surpassed training revenue.<sup>3</sup> This shift has exposed a fundamental vulnerability in NVIDIA’s GPU architecture: the "Memory Wall," which limits the speed and efficiency of real-time, low-latency applications.<sup>1</sup>

Groq, founded by former Google TPU architect Jonathan Ross, developed the Language Processing Unit (LPU), a deterministic, SRAM-based architecture capable of inference speeds 10x faster than NVIDIA’s flagship GPUs for specific workloads.<sup>4</sup> By acquiring Groq’s technology and 80% of its workforce, NVIDIA is preemptively neutralizing its most potent architectural rival while securing the "speed" component necessary for the next generation of "Agentic AI".<sup>1</sup>

The premium paid—nearly 3x Groq’s September 2025 valuation of $6.9 billion—reflects the defensive urgency to prevent this technology from falling into the hands of hyperscalers (Google, Microsoft) or merchant silicon rivals (AMD).<sup>6</sup> While the deal structure is designed to bypass immediate antitrust blockades by leaving the Groq corporate entity intact as a service provider, it carries significant regulatory tail risks.<sup>8</sup>

This memorandum provides an exhaustive analysis of the transaction, detailing the technological divergence between GPU and LPU architectures, the economic implications for the semiconductor value chain, and the strategic roadmap for integrating Groq’s innovations into NVIDIA’s upcoming "Vera Rubin" architecture.

## Part I: The Macro-Strategic Context

To fully appreciate the rationale behind a $20 billion expenditure for a company with relatively modest revenue, one must understand the seismic shifts occurring in the underlying economics of artificial intelligence. The industry is transitioning from a capital-expenditure-heavy "Training Phase" to an operational-expenditure-heavy "Inference Phase."

### 1.1 The Inference Flip and the Latency Crisis

For the decade spanning 2015 to 2025, the semiconductor industry was defined by the race to train larger models. This favored NVIDIA’s Graphics Processing Unit (GPU) architecture, which excels at massive parallel throughput. The A100 and H100 chips became the "shovels" in the generative AI gold rush, optimized to ingest terabytes of data and update billions of parameters over weeks or months. In this regime, latency (the time it takes to process a single instruction) was secondary to throughput (the total amount of data processed per second).<sup>9</sup>

However, the deployment of Large Language Models (LLMs) into consumer and enterprise applications has fundamentally altered the performance metrics that matter. We are entering the era of "Agentic AI"—systems that do not merely answer questions but perform actions, reason through complex multi-step problems, and interact vocally with humans in real-time.

The Speed Threshold:

Human conversation operates with a latency of roughly 200 milliseconds. Gaps in silence longer than this feel unnatural. For an AI to function as a seamless voice assistant or a real-time coding partner, it must generate text faster than human speech (approx. 150 words per minute) and process "Chain of Thought" reasoning almost instantly.5

Current GPU architectures face a physical limitation in achieving this. On a standard NVIDIA H100 cluster, generating a response involves moving data back and forth between the compute core and the external High Bandwidth Memory (HBM). This round-trip introduces latency. While GPUs are incredibly efficient at processing millions of requests in parallel (large batch sizes), they are inefficient at processing a single request instantly (batch size 1).<sup>5</sup>

By late 2025, the market signaled that the value of "instant" inference for financial trading, autonomous systems, and digital humans was skyrocketing. NVIDIA faced a risk: its hardware was perfect for *building* the brain, but potentially too slow for *using* it in time-critical scenarios. Groq’s LPU, designed specifically to eliminate this bottleneck, threatened to bifurcate the market, leaving NVIDIA with the training workload while Groq captured the high-value, real-time inference workload.<sup>3</sup>

### 1.2 The "Memory Wall" Physics

The central technical challenge driving this acquisition is the "Memory Wall." This term describes the growing disparity between the speed at which chips can calculate (compute) and the speed at which they can fetch data (memory bandwidth).

The GPU Bottleneck (HBM):

NVIDIA’s architecture relies on High Bandwidth Memory (HBM3e). While HBM is a marvel of engineering, delivering roughly 3.35 TB/s to 8 TB/s of bandwidth per chip, it resides outside the compute die on a silicon interposer.5 Every time the GPU needs to access a weight parameter from the model, it must cross the physical distance between the memory stack and the processor. In the context of light-speed electronics, this distance is an abyss. It creates latency and consumes significant energy.9

The LPU Solution (SRAM):

Groq solved this by reverting to a different memory hierarchy. Instead of external memory, Groq utilizes Static Random Access Memory (SRAM) interwoven directly with the processor cores on the main silicon die.

-   **Bandwidth:** This allows for bandwidths exceeding **80 TB/s**, an order of magnitude higher than HBM.<sup>5</sup>

-   **Access Time:** Data access is effectively instantaneous, occurring in single clock cycles rather than hundreds.

The trade-off is density. SRAM requires six transistors per bit of data, whereas DRAM (used in HBM) requires only one. Consequently, a single Groq chip holds only **230 MB** of memory, compared to **80 GB - 141 GB** on an NVIDIA H100 or H200.<sup>11</sup> To run a large model like Llama 3 70B, which requires roughly 140 GB of memory, one must connect approximately 576 Groq chips together in a massive, rack-scale computer.<sup>5</sup>

Despite this density disadvantage, the *speed* advantage is so profound for inference that Groq was winning contracts where latency was the primary KPI. NVIDIA’s acquisition is an acknowledgement that for the next phase of AI, overcoming the Memory Wall via SRAM integration—even at the cost of density—is a necessary architectural evolution.<sup>1</sup>

## Part II: The Target — Groq Inc.

To evaluate the $20 billion valuation, we must dissect the target’s provenance, technology, and market position prior to the deal.

### 2.1 Provenance: The Google TPU Lineage

Groq was founded in 2016 by Jonathan Ross, a former Google engineer who was instrumental in the creation of the Tensor Processing Unit (TPU). The TPU was Google’s internal response to NVIDIA, a custom ASIC (Application Specific Integrated Circuit) designed to accelerate machine learning. Ross’s work on the TPU gave him deep insight into the inefficiencies of using general-purpose GPUs for AI.<sup>1</sup>

Ross left Google with a radical premise: hardware should be "software-defined." Instead of building complex hardware that manages instruction flow (like a CPU or GPU with caches, branch predictors, and out-of-order execution), he proposed building simple, massive hardware that is entirely controlled by the compiler. This philosophy became the foundation of Groq’s "Deterministic" architecture.<sup>4</sup>

### 2.2 Technology Deep Dive: The Language Processing Unit (LPU)

The LPU is fundamentally different from a GPU. It is a Single Instruction Multiple Data (SIMD) processor that operates on a "Time-Deterministic" basis.

Deterministic Execution:

In an NVIDIA GPU, the hardware makes real-time decisions about which task to run next based on data availability. This introduces "jitter"—unpredictable variations in processing time. In a Groq LPU, the software compiler plans the exact nanosecond every electron will move before the program even starts.

-   **The Conveyor Belt Analogy:** If a GPU is a traffic circle where cars (data) merge and yield dynamically, an LPU is a high-speed train system where every arrival is scheduled to the millisecond. There are no collisions, no waiting, and no arbitration.<sup>4</sup>

-   **Result:** This leads to zero "tail latency." The 99th percentile response time is the same as the average response time. This is critical for synchronized systems like self-driving cars or high-frequency trading algorithms.<sup>5</sup>

Performance Metrics:

Benchmarks from late 2025 demonstrated the LPU’s dominance in "Throughput per User":

-   **Tokens Per Second (Llama 3 70B):** Groq achieved &gt;800 T/s, peaking at 1,600 T/s in optimized clusters.

-   **NVIDIA H100:** Typically delivered 100–200 T/s depending on quantization and batching.

-   **Time to First Token (TTFT):** Groq consistently delivered &lt;0.2 seconds, providing an "instant" feel, versus 0.5–1.0 seconds for GPU clusters.<sup>5</sup>

### 2.3 The "Achilles Heel": Scalability and Cost

The weakness of Groq’s approach was the sheer physical footprint required. Because of the SRAM density limit (230MB per chip), replacing a single 8-GPU NVIDIA server (which fits in 4 rack units) required multiple full racks of Groq chips to hold the same model.<sup>5</sup>

-   **CapEx Implication:** While Groq claimed a better "Cost Per Token" due to high throughput, the initial capital expenditure to buy hundreds of chips was a barrier for smaller enterprises.

-   **Power Density:** The energy required to power 576 chips, even if each is efficient, presented data center cooling challenges distinct from the concentrated heat of 8 GPUs.<sup>10</sup>

Despite these issues, the "Inference Flip" meant that for hyperscalers and latency-sensitive enterprises, the cost of *slowness* was higher than the cost of hardware. Groq was beginning to win.

## Part III: The Transaction Architecture

NVIDIA’s legal and strategic teams structured this deal with extreme precision to navigate a regulatory minefield.

### 3.1 The "License and Acqui-Hire" Structure

NVIDIA did not acquire Groq Inc. Instead, it executed two simultaneous agreements:

1.  **Asset License:** A perpetual, non-exclusive license to Groq’s patents, architecture designs, and compiler software for $20 billion cash.<sup>1</sup>

2.  **Human Capital Transfer:** The hiring of founder Jonathan Ross, President Sunny Madra, and approximately 80% of the engineering staff.<sup>1</sup>

**Strategic Rationale for Structure:**

-   **Antitrust Evasion:** By not acquiring the corporate entity, NVIDIA avoids the automatic "merger" classification that triggers HSR (Hart-Scott-Rodino) waiting periods and intensive scrutiny in some jurisdictions. The narrative is that Groq remains an independent competitor.<sup>13</sup>

-   **Liability Segmentation:** NVIDIA leaves behind the legacy corporate shell, which retains existing contracts and liabilities, including the operational complexity of the GroqCloud service.

-   **The Microsoft Precedent:** This mirrors Microsoft’s March 2024 deal with Inflection AI, where it hired Mustafa Suleyman and licensed the models for $650 million. NVIDIA has scaled this playbook to $20 billion.<sup>2</sup>

### 3.2 Valuation Analysis

The $20 billion price tag represents a massive step-up in valuation.

| **Valuation Event** | **Date**       | **Valuation**     | **Investor Lead**                      |
|---------------------|----------------|-------------------|----------------------------------------|
| **Series D**        | August 2024    | $2.8 Billion      | BlackRock Private Equity <sup>15</sup> |
| **Series E**        | September 2025 | $6.9 Billion      | Disruptive / BlackRock <sup>3</sup>    |
| **NVIDIA Deal**     | December 2025  | **$20.0 Billion** | NVIDIA (Cash) <sup>1</sup>             |

**Implied Multiples:**

-   **Step-Up:** 2.9x over the 3-month-old Series E valuation.

-   **Revenue Multiple:** Assuming Groq’s optimistic 2025 revenue target of $500 million was met <sup>17</sup>, the deal represents a **40x Revenue Multiple**.

**Justification for Premium:**

-   **The "Killer Acquisition" Premium:** NVIDIA is paying to remove a competitor. If Groq continued to grow, it could have eroded NVIDIA’s inference market share, which is projected to be worth hundreds of billions.

-   **The "Talent" Premium:** Silicon architects of Jonathan Ross’s caliber are exceedingly rare. The cost of *not* having him (or worse, having him join Google or AMD) justifies billions in retention value.<sup>7</sup>

-   **The "Time" Premium:** Building a mature compiler stack for deterministic hardware takes 5-7 years. NVIDIA bought this timeline instantly.<sup>13</sup>

### 3.3 The Remaining Entity: "Zombie Groq"

The legacy entity, likely to be rebranded or operated simply as "GroqCloud," will be led by Simon Edwards (former CFO). It retains the physical hardware currently deployed and the rights to use the IP (non-exclusively).

-   **Strategic Function:** Its primary purpose is to fulfill the regulatory requirement of maintaining a competitor in the market. It also must honor the $1.5 billion infrastructure deal with Saudi Arabia, which likely has sovereignty clauses preventing the hardware from being moved or shut down.<sup>1</sup>

-   **Future Viability:** Without its engineering core, this entity is effectively a "zombie"—capable of operations but incapable of innovation. It will likely function as a specialized cloud service provider until its hardware becomes obsolete.<sup>2</sup>

## Part IV: Competitive Implications

The shockwaves of this deal effectively reshape the competitive landscape for the remainder of the decade.

### 4.1 Neutralizing the AMD Threat

Advanced Micro Devices (AMD) has been the primary beneficiary of NVIDIA’s supply constraints. Its MI300 and upcoming MI400 chips compete on *capacity*—packing more HBM memory per chip to lower the cost of running large models.<sup>19</sup>

-   **The Shift:** AMD’s value proposition was "cheaper per token." Groq’s value proposition was "faster per token." By acquiring Groq, NVIDIA now owns the high ground on speed.

-   **The Squeeze:** AMD is now sandwiched. It cannot beat NVIDIA on training (CUDA moat), and it can no longer easily pivot to beat NVIDIA on latency (since NVIDIA now owns the premier latency architecture). AMD is forced to compete solely on price/performance for bulk, non-real-time workloads.<sup>3</sup>

### 4.2 The Hyperscaler Checkmate

Google (TPU), Amazon (Trainium/Inferentia), and Microsoft (Maia) have been building custom chips to reduce their "Nvidia Tax."

-   **Google's Loss:** Jonathan Ross was a key architect of the TPU. His return to NVIDIA is a symbolic and practical blow to Google’s hardware team. It signals that the "TPU architecture" lineage is now part of NVIDIA.<sup>7</sup>

-   **Hybrid Lock-in:** If NVIDIA successfully integrates Groq’s technology to offer a "Training + Instant Inference" rack, it reduces the incentive for hyperscalers to offload inference to their own chips. The TCO (Total Cost of Ownership) argument for custom silicon weakens if NVIDIA’s hardware becomes significantly more efficient at inference.<sup>10</sup>

### 4.3 The Startup Extinction Event

The semiconductor startup ecosystem (Cerebras, SambaNova, Tenstorrent) faces a new reality.

-   **Valuation Floor:** The $20 billion price tag sets a high benchmark. Cerebras, planning an IPO, will likely demand a valuation exceeding this figure, arguing their wafer-scale engine offers both training and inference.<sup>21</sup>

-   **Exit Strategy:** The deal signals that "exit to incumbent" is a viable path, potentially triggering a wave of M&A activity as AMD, Intel, and Qualcomm scramble to buy the remaining independent AI chip startups to stay relevant.<sup>3</sup>

## Part V: Regulatory & Antitrust Risks

While the deal structure is clever, it is not immune to challenge. This transaction will be a litmus test for the "Maverick Theory" of antitrust enforcement.

### 5.1 The "Maverick Firm" Theory

Antitrust law (specifically in the US and EU) disfavors acquisitions that remove a "Maverick"—a firm that plays a disruptive role in the market, forcing the dominant player to innovate or lower prices.

-   **Groq as Maverick:** Groq’s low pricing and high speed forced NVIDIA to accelerate its own roadmap and potentially lower prices on inference-class cards. By absorbing Groq, NVIDIA removes this competitive pressure.<sup>22</sup>

-   **Investigation Risk:** The DOJ has already signaled interest in "regulatory bypass" deals. If they determine that Groq Inc. (the remaining entity) is a sham competitor, they could sue to unwind the talent transfer or impose heavy fines.<sup>22</sup>

### 5.2 Global Scrutiny

-   **China:** China’s SAMR (State Administration for Market Regulation) has previously used merger reviews to extract concessions. While this is an asset deal, NVIDIA’s deep exposure to the Chinese supply chain makes it vulnerable. However, given the US restrictions on selling high-end chips to China, Beijing’s leverage is somewhat reduced compared to the Mellanox era.<sup>23</sup>

-   **Europe/UK:** The UK CMA blocked the ARM deal on "ecosystem" concerns. They may view NVIDIA’s control of both the *software* (CUDA) and the *hardware* (GPU + LPU) as creating an insurmountable barrier to entry for UK-based chip designers (like Graphcore, though Graphcore is largely effectively defunct or acquired by Softbank).<sup>14</sup>

### 5.3 The "National Champion" Defense

NVIDIA will likely leverage the geopolitical angle. By consolidating Groq’s "American" IP under NVIDIA (an American champion), they protect the technology from foreign investment or acquisition. The "Trump Administration" (referenced in snippets) is likely to favor strengthening a US national champion over abstract antitrust concerns, potentially providing political cover for the deal.<sup>8</sup>

## Part VI: Integration Roadmap — Project Vera Rubin

The ultimate value of this deal lies in the integration of Groq’s "Deterministic Core" into NVIDIA’s roadmap.

### 6.1 The "Rubin" Architecture (2026/2027)

NVIDIA’s next-generation architecture, codenamed "Rubin" (after astronomer Vera Rubin), is scheduled for 2026.

-   **The Hybrid Vision:** We anticipate the emergence of a "Rubin-I" (Inference) or "Rubin Ultra" chip that incorporates Groq’s SRAM-heavy design. Imagine a GPU that has the traditional massive HBM memory for bulk storage, but also a dedicated "LPU Tile" on the die with massive SRAM for executing the latency-sensitive parts of the model (like the decoding step of an LLM).<sup>14</sup>

-   **Software Unification:** The hardest part is software. NVIDIA must integrate Groq’s compiler (which requires knowing everything in advance) with CUDA (which is dynamic). The goal is a "Unified Compute Fabric" where a developer writes code once, and the system automatically routes latency-sensitive tasks to the LPU cores and throughput-heavy tasks to the GPU cores.<sup>4</sup>

### 6.2 The Cloud Strategy

NVIDIA is likely to deprecate GroqCloud over time or merge it into its "DGX Cloud" service. By offering "NVIDIA Real-Time Inference" as a premium tier in DGX Cloud, NVIDIA can capture the high-margin recurring revenue from customers building voice agents and trading bots, effectively eating into the market share of AWS and Azure.<sup>14</sup>

## Part VII: Investment Conclusion

**Rating: BUY (Long-Term Strategic Accumulation)**

NVIDIA’s $20 billion acquisition of Groq is expensive, aggressive, and fraught with regulatory risk. However, it is fundamentally the correct strategic move to secure the company’s dominance for the next decade.

**The Bull Case:**

1.  **Moat Expansion:** NVIDIA creates the only hardware platform capable of handling the entire AI lifecycle—from massive training runs to nanosecond-latency inference.

2.  **Margin Protection:** By owning the superior architecture, NVIDIA can maintain its &gt;70% gross margins in the inference market, resisting the commoditization pressure from AMD and hyperscalers.

3.  **Talent Monopoly:** Securing the team that built the TPU and LPU ensures the smartest minds in silicon are working for NVIDIA, not against it.

**The Bear Case:**

1.  **Regulatory Breakup:** Forced divestiture would be messy and distracting.

2.  **Integration Failure:** Merging two diametrically opposite architectural philosophies (Dynamic vs. Deterministic) could fail, wasting the $20 billion and stalling the roadmap.

3.  **SRAM Scaling Limits:** If AI models grow too large, the cost of SRAM-based inference might remain too high, rendering the tech a niche solution.

Final Verdict:

NVIDIA has effectively bought "latency insurance." As the world moves to Agentic AI, the value of time (latency) becomes infinite. Groq owned the technology of time. Now, NVIDIA does. This deal cements NVIDIA not just as a chip company, but as the inescapable substrate of the Intelligence Economy.

### Data Appendix: Technical Comparison

| **Feature**          | **NVIDIA Blackwell (Current)** | **Groq LPU (Acquired Tech)** | **NVIDIA Rubin (Future Hybrid)** |
|----------------------|--------------------------------|------------------------------|----------------------------------|
| **Primary Memory**   | HBM3e (Off-Chip)               | SRAM (On-Chip)               | HBM4 + Expanded SRAM             |
| **Bandwidth**        | \~8 TB/s                       | \~80 TB/s                    | &gt;100 TB/s (Effective)         |
| **Latency Profile**  | Probabilistic (Jitter)         | Deterministic (Zero Jitter)  | Tiered / Adaptive                |
| **Batch Efficiency** | High Batch (Throughput)        | Batch-1 (Latency)            | Universal                        |
| **Scheduling**       | Hardware Dynamic               | Compiler Static              | Software Defined                 |
| **Ideal Workload**   | Training / Offline Batch       | Real-Time Voice / Trading    | End-to-End Agentic AI            |

Sources: <sup>4</sup>

#### Works cited

1.  Nvidia's $20 Billion Strategic Integration of Groq: A New Era for AI Inference, accessed December 27, 2025, [<u>https://markets.financialcontent.com/wral/article/marketminute-2025-12-25-nvidias-20-billion-strategic-integration-of-groq-a-new-era-for-ai-inference</u>](https://markets.financialcontent.com/wral/article/marketminute-2025-12-25-nvidias-20-billion-strategic-integration-of-groq-a-new-era-for-ai-inference)

2.  Nvidia Solidifies AI Dominance with Landmark $20 Billion Groq Strategic "Acqui-Hire", accessed December 27, 2025, [<u>https://markets.financialcontent.com/stocks/article/marketminute-2025-12-26-nvidia-solidifies-ai-dominance-with-landmark-20-billion-groq-strategic-acqui-hire</u>](https://markets.financialcontent.com/stocks/article/marketminute-2025-12-26-nvidia-solidifies-ai-dominance-with-landmark-20-billion-groq-strategic-acqui-hire)

3.  NVIDIA's $20 Billion Groq Gambit: The Dawn of the Inference Consolidation Era, accessed December 27, 2025, [<u>https://markets.financialcontent.com/stocks/article/marketminute-2025-12-26-nvidias-20-billion-groq-gambit-the-dawn-of-the-inference-consolidation-era</u>](https://markets.financialcontent.com/stocks/article/marketminute-2025-12-26-nvidias-20-billion-groq-gambit-the-dawn-of-the-inference-consolidation-era)

4.  Nvidia Secures AI Inference Dominance with Landmark $20 Billion Groq Licensing Deal, accessed December 27, 2025, [<u>https://markets.financialcontent.com/wral/article/tokenring-2025-12-25-nvidia-secures-ai-inference-dominance-with-landmark-20-billion-groq-licensing-deal</u>](https://markets.financialcontent.com/wral/article/tokenring-2025-12-25-nvidia-secures-ai-inference-dominance-with-landmark-20-billion-groq-licensing-deal)

5.  Groq's Deterministic Architecture is Rewriting the Physics of AI Inference - Medium, accessed December 27, 2025, [<u>https://medium.com/the-low-end-disruptor/groqs-deterministic-architecture-is-rewriting-the-physics-of-ai-inference-bb132675dce4</u>](https://medium.com/the-low-end-disruptor/groqs-deterministic-architecture-is-rewriting-the-physics-of-ai-inference-bb132675dce4)

6.  Nvidia partners AI hardware startup Groq; hires its key engineers and founder, accessed December 27, 2025, [<u>https://timesofindia.indiatimes.com/technology/tech-news/nvidia-partners-ai-hardware-startup-groq-hires-its-key-engineers-and-founder/articleshow/126173056.cms</u>](https://timesofindia.indiatimes.com/technology/tech-news/nvidia-partners-ai-hardware-startup-groq-hires-its-key-engineers-and-founder/articleshow/126173056.cms)

7.  How 'Google fear and threat' just made Nvidia spend $20 billion, accessed December 27, 2025, [<u>https://timesofindia.indiatimes.com/technology/tech-news/how-google-fear-and-threat-just-made-nvidia-just-spend-20-billion/articleshow/126188810.cms</u>](https://timesofindia.indiatimes.com/technology/tech-news/how-google-fear-and-threat-just-made-nvidia-just-spend-20-billion/articleshow/126188810.cms)

8.  Nvidia to license Groq’s AI chip technology and hire its CEO, accessed December 27, 2025, [<u>https://www.financialexpress.com/life/technology-nvidia-to-license-groqs-ai-chip-technology-and-hire-its-ceo-4088679/</u>](https://www.financialexpress.com/life/technology-nvidia-to-license-groqs-ai-chip-technology-and-hire-its-ceo-4088679/)

9.  Twenty Billion for Nanoseconds: What Nvidia's Groq Deal Says ..., accessed December 27, 2025, [<u>https://medium.com/@bailey55015/twenty-billion-for-nanoseconds-what-nvidias-groq-deal-says-about-the-value-of-speed-453ab1608e14</u>](https://medium.com/@bailey55015/twenty-billion-for-nanoseconds-what-nvidias-groq-deal-says-about-the-value-of-speed-453ab1608e14)

10. Nvidia's $20B Groq Bet: Why Inference-First Chips Change Everything - Medium, accessed December 27, 2025, [<u>https://medium.com/@spallaprolu/nvidias-20b-groq-bet-why-inference-first-chips-change-everything-303f2ecd684c</u>](https://medium.com/@spallaprolu/nvidias-20b-groq-bet-why-inference-first-chips-change-everything-303f2ecd684c)

11. Nvidia enters licensing deal with Groq, D.A. Davidson questions move By Investing.com, accessed December 27, 2025, [<u>https://www.investing.com/news/analyst-ratings/nvidia-enters-licensing-deal-with-groq-da-davidson-questions-move-93CH-4423158</u>](https://www.investing.com/news/analyst-ratings/nvidia-enters-licensing-deal-with-groq-da-davidson-questions-move-93CH-4423158)

12. The main problem with the Groq LPUs is, they don't have any HBM on them at all. ... - Hacker News, accessed December 27, 2025, [<u>https://news.ycombinator.com/item?id=39431989</u>](https://news.ycombinator.com/item?id=39431989)

13. NVDA Stock Surges After NVIDIA's $20B Groq AI Deal - MarketBeat, accessed December 27, 2025, [<u>https://www.marketbeat.com/originals/nvidias-20b-groq-deal-is-a-warning-shot-to-ai-rivals/</u>](https://www.marketbeat.com/originals/nvidias-20b-groq-deal-is-a-warning-shot-to-ai-rivals/)

14. Nvidia's $20B Groq Deal: Strategy, LPU Tech & Antitrust \| IntuitionLabs, accessed December 27, 2025, [<u>https://intuitionlabs.ai/articles/nvidia-groq-ai-inference-deal</u>](https://intuitionlabs.ai/articles/nvidia-groq-ai-inference-deal)

15. Nvidia Acquires Tech and Talent From Inference Chip Maker Groq \| PYMNTS.com, accessed December 27, 2025, [<u>https://www.pymnts.com/artificial-intelligence-2/2025/nvidia-acquires-tech-and-talent-from-inference-chip-maker-groq/</u>](https://www.pymnts.com/artificial-intelligence-2/2025/nvidia-acquires-tech-and-talent-from-inference-chip-maker-groq/)

16. Nvidia's $20B Groq Deal: Strategy, LPU Tech & Antitrust - IntuitionLabs, accessed December 27, 2025, [<u>https://intuitionlabs.ai/pdfs/nvidia-s-20b-groq-deal-strategy-lpu-tech-antitrust.pdf</u>](https://intuitionlabs.ai/pdfs/nvidia-s-20b-groq-deal-strategy-lpu-tech-antitrust.pdf)

17. Nvidia licenses Groq inference technology, Groq executives join chipmaker (NVDA:NASDAQ) \| Seeking Alpha, accessed December 27, 2025, [<u>https://seekingalpha.com/news/4535300-nvidia-licenses-groq-inference-technology-groq-executives-join-chipmaker</u>](https://seekingalpha.com/news/4535300-nvidia-licenses-groq-inference-technology-groq-executives-join-chipmaker)

18. From GPUs to LPUs – Where Groq Fits Among Nvidia, AMD, and Cerebras, accessed December 27, 2025, [<u>https://news.future-of-computing.com/p/from-gpus-to-lpus-where-groq-fits-among-nvidia-amd-and-cerebras</u>](https://news.future-of-computing.com/p/from-gpus-to-lpus-where-groq-fits-among-nvidia-amd-and-cerebras)

19. Could AMD Finally Challenge Nvidia With Its MI400 AI Chips? \| The Motley Fool, accessed December 27, 2025, [<u>https://www.fool.com/investing/2025/06/20/could-amd-finally-challenge-nvidia-with-its-mi400/</u>](https://www.fool.com/investing/2025/06/20/could-amd-finally-challenge-nvidia-with-its-mi400/)

20. Nvidia's $20 Billion Strategic Masterstroke: Securing the Future of AI Inference with Groq, accessed December 27, 2025, [<u>https://markets.financialcontent.com/stocks/article/marketminute-2025-12-26-nvidias-20-billion-strategic-masterstroke-securing-the-future-of-ai-inference-with-groq</u>](https://markets.financialcontent.com/stocks/article/marketminute-2025-12-26-nvidias-20-billion-strategic-masterstroke-securing-the-future-of-ai-inference-with-groq)

21. Nvidia buying AI chip startup Groq's assets for about $20 billion in largest deal on record : r/CerebrasSystems - Reddit, accessed December 27, 2025, [<u>https://www.reddit.com/r/CerebrasSystems/comments/1puynnv/nvidia\_buying\_ai\_chip\_startup\_groqs\_assets\_for/</u>](https://www.reddit.com/r/CerebrasSystems/comments/1puynnv/nvidia_buying_ai_chip_startup_groqs_assets_for/)

22. The "Quasi-Merger" Crackdown: How US Regulators are Redrawing the Map for Big Tech's AI Ambitions - Markets & Stocks - The Chronicle-Journal, accessed December 27, 2025, [<u>http://markets.chroniclejournal.com/chroniclejournal/article/marketminute-2025-12-26-the-quasi-merger-crackdown-how-us-regulators-are-redrawing-the-map-for-big-techs-ai-ambitions</u>](http://markets.chroniclejournal.com/chroniclejournal/article/marketminute-2025-12-26-the-quasi-merger-crackdown-how-us-regulators-are-redrawing-the-map-for-big-techs-ai-ambitions)

23. Groq: Nvidia's $20 Billion Bet on AI Inference - EE Times, accessed December 27, 2025, [<u>https://www.eetimes.com/groq-nvidias-20-billion-bet-on-ai-inference/</u>](https://www.eetimes.com/groq-nvidias-20-billion-bet-on-ai-inference/)

24. Nvidia Nudges Higher as Groq Deal Targets the Inference Side of AI Growth \| Investing.com, accessed December 27, 2025, [<u>https://www.investing.com/analysis/nvidia-nudges-higher-as-groq-deal-targets-the-inference-side-of-ai-growth-200672392</u>](https://www.investing.com/analysis/nvidia-nudges-higher-as-groq-deal-targets-the-inference-side-of-ai-growth-200672392)

25. CNBC Today On NVIDIA Stock, NVIDIA Groq Deal - NVDA Update, accessed December 27, 2025, [<u>https://www.youtube.com/watch?v=8CfumWfYqUE</u>](https://www.youtube.com/watch?v=8CfumWfYqUE)

26. NVIDIA confirms the Rubin architecture for 2026 - Instant Gaming News, accessed December 27, 2025, [<u>https://news.instant-gaming.com/en/articles/14555-nvidia-confirms-the-rubin-architecture-for-2026</u>](https://news.instant-gaming.com/en/articles/14555-nvidia-confirms-the-rubin-architecture-for-2026)
