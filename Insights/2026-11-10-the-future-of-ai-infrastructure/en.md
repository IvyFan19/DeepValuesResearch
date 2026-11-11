---
title: "Re-Architecting Infrastructure for the Agentic AI Era: Inside Google Cloud’s Co-Designed Hardware and Software Stack"
date: "2026-11-10"
lang: "en"
category: "ai"
tickers: ["AMD"]
notebook_id: "6d8f2e3d-1ef8-4b35-a56f-12853b2c3614"
source_urls:
  - title: "The Future of AI Infrastructure"
    url: "https://www.youtube.com/watch?v=pabDkNR7jIs"
youtube:
  - title: "Google's TPU Rebuild: Why AI Agents Need 55x More Compute"
    url: "https://youtu.be/8wO2pFKGxpU"
    lang: "en"
  - title: "Google為何把AI晶片射上太空？算力需求將暴增55倍"
    url: "https://youtu.be/dNSQ8HNafyI"
    lang: "zh"
podcast:
  - title: "Google's TPU Rebuild: Why AI Agents Need 55x More Compute"
    url: "https://open.spotify.com/episode/6MBMF32OxXP4pA7k59tyA2"
    lang: "en"
  - title: "Google為何把AI晶片射上太空？算力需求將暴增55倍"
    url: "https://open.spotify.com/episode/4WIQyRxPmQ0yhHg9shTTJi"
    lang: "zh"
generated_by: "NotebookLM + DeepValues editors"
disclosure: "AI-assisted"
---

# Re-Architecting Infrastructure for the Agentic AI Era: Inside Google Cloud’s Co-Designed Hardware and Software Stack

As artificial intelligence transitions from human-initiated prompts to autonomous, multi-step agentic workflows, enterprise computing infrastructure is undergoing a fundamental structural evolution. Unlike brief human search queries, autonomous software agents operate in continuous reasoning loops—spawning subagents, executing dynamic code, and consuming millions of tokens across multi-day tasks. To sustain this exponential surge in compute intensity, Google Cloud has engineered its 8th generation Tensor Processing Unit (TPU) ecosystem around comprehensive hardware-software co-design. Key architectural advancements—including the low-diameter Board Fly network topology, specialized TPU 8TX and TPU 8i Max hardware configurations, native open-source framework integrations, and the dedicated Agent Compute Engine (ACE) execution runtime—address critical bottlenecks in memory bandwidth, network latency, and sandbox security. This co-designed approach optimizes compute density, improves token economics, and enforces the hardware-rooted security boundaries necessary to deploy enterprise software agents at scale.

---

## The Inflection Point: Transitioning from Human-Scale Queries to Agentic Workflows

The fundamental nature of enterprise compute demand is shifting from human-initiated interactions to continuous multi-agent execution loops. Standard human interactions with artificial intelligence models typically involve brief back-and-forth exchanges consuming approximately 1,000 tokens per interaction. In contrast, autonomous agentic workflows require systems to receive a high-level objective, decompose tasks, write code, query external software systems, inspect outputs, and iteratively self-correct over multi-day operations.

Executing these extended workflows transforms model inference into an ongoing execution loop. A single objective can trigger dozens of specialized subagents and hundreds of distinct model queries, causing token consumption per task to scale from thousands to millions. As a result, agent-driven traffic surged by over 7,800% in the past year alone. Model inference now accounts for 50% to 70% of total artificial intelligence (AI) compute consumption across enterprise workloads, up from 40% two years prior.

Long-term industry models project that global token demand will multiply 24-fold by 2030, reaching over 120 quadrillion tokens per month. Supporting this expansion requires a 55-fold surge in compute intensity. Traditional data center provisioning, networking topologies, and software runtimes—originally designed for deterministic "systems of record"—face severe structural bottlenecks when adapted to agentic "systems of action." As Amin Vahdat noted, "An agent receives an objective, thinks, then acts." Meeting these continuous operational demands requires re-architecting every layer of the technology stack, from data center power delivery to silicon compiler runtimes.

---

## Anatomy of Custom Silicon: The Six Engineering Principles of the TPU

Google Cloud’s domain-specific processor strategy originated during a scaling bottleneck in 2013. Internal projections revealed that if every Android user utilized Google Voice search for just three minutes per day, the underlying neural network calculations would require doubling Google’s entire data center footprint. To eliminate the need for such capital expansion, engineers developed a domain-specific processor tailored specifically for matrix mathematics: the Tensor Processing Unit (TPU). Introduced in 2015, the original air-cooled TPU v1 was a 75-Watt Peripheral Component Interconnect Express (PCIe) card delivering 30 times the throughput of contemporary general-purpose processors of that era.

Over eight generations of custom silicon, the underlying TPU execution model has relied on six foundational architectural principles:

1.  **Fewer, Larger Cores:** Hardware-level thread schedulers and dynamic branching logic are omitted. Instead, execution planning is controlled explicitly by software compilers.
2.  **Systolic Arrays:** Data streams continuously through a physical grid of multipliers, reusing values cycle after cycle rather than repeatedly fetching them from register files.
3.  **Compiler-Controlled Memory:** Traditional hardware caches are replaced with explicit compiler-managed memory movement to prevent unpredictable latency spikes.
4.  **Optical Circuit Switches (OCS):** Inter-chip communication uses light beams reflected by tiny mirrors, bypassing the higher power draw and potential packet drops of traditional electrical switches.
5.  **Compact Number Formats:** Numerical precision relies on specialized, efficient representations such as bfloat16 and Native Floating Point 4 (FP4), maximizing mathematical throughput per Watt while maintaining bitwise determinism.
6.  **Direct Liquid Cooling:** Clamped liquid cooling cold plates extract heat directly at the silicon surface, enabling maximum operational throughput without thermal throttling.

The 8th generation training board features dual multi-die compute packages flanked by 12 High Bandwidth Memory (HBM3E) stacks. To prevent electrical delivery bottlenecks, heavy copper power planes step down voltage directly beside the silicon. Inter-chip communication relies on a multidimensional copper interconnect ring operating at 19.2 terabits per second (Tbps) bidirectional per chip. At the edge of the board where copper interconnects transition to optical signals for OCS routing, liquid-cooled cold plates clamp directly across the optical transceivers. Scaled to a 9,600-chip superpod, this platform provides nearly three times the compute performance of prior generations at 2.7 times lower cost.

---

## Overcoming Inference Latency and the Memory Wall: Board Fly, TPU 8TX, and TPU 8i Max

Agentic inference introduces severe network latency and memory bandwidth limitations. Standard accelerator clusters frequently deploy a 3D torus network topology, which routes data sequentially through neighboring chips. While highly effective for synchronous pre-training loops, a 3D torus requires up to 16 hops to traverse a cluster. In distributed agentic inference, where processors must coordinate partial mathematical sums across multiple chips for every token generated, a 16-hop delay introduces operational latency stalls.

To resolve this latency penalty, Google Cloud introduced the **Board Fly** network topology for its 8th generation inference systems. Board Fly is a hierarchical, low-diameter mesh topology that establishes direct optical shortcuts across circuit boards and data center racks. This architecture reduces the worst-case network diameter from 16 hops down to 7 hops, cutting inter-chip communication latency by up to 50%.

To address specialized enterprise execution requirements, the 8th generation hardware ecosystem incorporates two complementary inference configurations alongside the single-die TPU 8i baseline (which features 288GB of HBM):

### Hardware-Enforced Confidentiality: TPU 8TX
The TPU 8TX configuration provides 12.6 petaflops of Native FP4 compute performance and 216GB of HBM. It moves security boundaries from software runtimes down to hardware silicon. Operating in conjunction with custom Advanced Micro Devices (AMD) host processors, the system enforces hardware-level PCIe link encryption, cryptographic attestation, and secure memory enclaves. This structure guarantees that proprietary model weights and sensitive enterprise agent data remain encrypted during compute execution, delivering twice lower latency compared to TPU 8t.

### Overcoming the Memory Wall: TPU 8i Max
Long-context reasoning loops often saturate memory bandwidth as Key-Value (KV) caches expand. The TPU 8i Max addresses this bottleneck by integrating two compute dies into a single package, providing 384GB of HBM—a 33% increase over the baseline 288GB HBM capacity found on TPU 8i.

The system provides 17.2 terabytes per second (TB/s) of HBM memory bandwidth (double that of TPU 8i) alongside 768MB of ultra-fast on-chip Static Random-Access Memory (SRAM) (double that of TPU 8i). This memory scaling functions like expanding a multi-lane highway: rather than requiring individual tokens to process faster, doubling the HBM memory bandwidth adds concurrent lanes. This allows higher numbers of parallel agents to read long context histories simultaneously without experiencing memory access bottlenecks. Furthermore, packaging two compute dies within a unified multi-chip module bypasses single-die reticle size limits during semiconductor fabrication, optimizing floating-point operations (flops), SRAM, and HBM bandwidth per square foot and per Watt inside the data center.

---

## Open Software Ecosystems and Co-Designed Inference Optimization

Hardware advancements require open software integration to operate efficiently in enterprise production environments. Google Cloud, in collaboration with Meta, developed `torch_tpu`, an integration that establishes TPUs as a native backend execution target for PyTorch framework code. This integration allows engineering teams to deploy unmodified PyTorch models directly onto TPU infrastructure. Additionally, native TPU support has been implemented for popular open-source inference serving engines, including vLLM and SGLang.

To maintain peak accelerator utilization during multi-step execution loops, Google Cloud developed two specific software optimizations:

*   **TPU Sync:** When an autonomous agent pauses to wait for external Application Programming Interface (API) tool calls or human intervention, TPU sync offloads its active working memory state from the accelerator directly to host server memory. The moment the external tool responds, the memory state streams back to the TPU, eliminating idle accelerator clock cycles.
*   **LMDB 1.0 (Inference Control Plane):** Integrated into the Google Kubernetes Engine (GKE) Inference Gateway, LMDB 1.0 supplies control plane primitives designed for long-context execution. It combines prefix cache-aware routing, disaggregated serving, and three-tier KV cache offloading (across accelerator memory, host system memory, and storage drives) to prevent system context dropping during multi-day agent operations.

This software ecosystem maintains operational flexibility across diverse hardware platforms. Enterprise infrastructure deployments can manage both Google TPUs and NVIDIA graphics processing units (GPUs)—such as General Availability instances of A5 powered by the NVIDIA Vera Rubin platform, and Google Distributed Cloud configurations powered by NVIDIA Blackwell—within a single unified control plane.

---

## The Execution Layer: Agent Compute Engine and Axion Processors

While accelerators handle matrix operations for reasoning, central processing units (CPUs) execute deterministic agent software actions. Scaling agentic workloads requires runtime execution environments that satisfy three key requirements: multi-layer security isolation, instant activation, and statefulness across operational pauses.

As Mark Lohmeyer observed, "When humans write code, it gets reviewed before it ever hits production." To handle code written dynamically by AI agents, Google Cloud engineered the **Agent Compute Engine (ACE)**.

ACE deploys each agent sandbox as a lightweight micro Virtual Machine (microVM) running on Cloud Hypervisor with a dedicated guest kernel written in memory-safe Rust. Network traffic is filtered out-of-band by an Agent Gateway that enforces precise domain allowlists, while Titanium Infrastructure Processing Units (IPUs) offload networking, storage, and line-rate hardware encryption onto dedicated silicon. When an agent pauses execution, ACE hibernates the microVM, halting compute consumption while persisting the complete working memory state and attached Hyperdisk block storage volumes. Upon resuming, the sandbox restores instantly without requiring an operating system reboot, allowing physical hosts to achieve operational densities of thousands of microVMs per server.

To drive open industry standardization, Google Cloud donated **Agent Substrate**—the open-source agent execution runtime for Kubernetes—to the Cloud Native Computing Foundation (CNCF). This open framework operates alongside enterprise governance components including Agent Identity, Agent Registry (for Model Context Protocol [MCP] tools), Agent Observability telemetry, and Token Management budget controls. At the hardware execution layer, these environments run across standard x86 processors as well as custom ARM-based **Axion** processors, which deliver up to 30% better price-performance than rival leading cloud instances, supported by Remote Direct Memory Access (RDMA) networking for 40% higher throughput.

---

## Energy Efficiency, Operational Limitations, and Industry Trade-offs

Scaling data center capacity to meet exponential token growth places severe demands on regional electrical power grids. Google Cloud facilities maintain a trailing 12-month average Power Usage Effectiveness (PUE) of 1.09, representing 83% less overhead energy usage than traditional industry averages. Through custom hardware co-design, its data centers deliver over three times the compute performance per unit of energy consumed compared to metrics from five years ago.

To explore computing models beyond terrestrial grid constraints, Google Cloud initiated **Project Suncatcher**, an experimental moonshot testing solar-powered TPUs in Low Earth Orbit (LEO). Four weeks into its initial prototype launch, engineering teams confirmed satellite contact and executed a successful space-to-Earth "Hello World" inference test. The flight is actively gathering performance data regarding cosmic radiation resistance and thermal dissipation within a vacuum environment. Next year, the project plans to launch a satellite pair to test high-bandwidth inter-satellite laser links. As Maria Biggs stated, "Turning this audacious idea into workable reality requires disciplined, step by step experimentation."

### Operational Limitations and Strategic Trade-offs
Despite these performance advancements, scaling co-designed infrastructure introduces specific technical trade-offs:

*   **Compiler Ecosystem Overhead:** Hardware architectures that omit dynamic thread schedulers depend heavily on specialized compiler optimization paths (`torch_tpu`, XLA). Managing custom compilation pipelines can require specialized software expertise compared to standard hardware target environments.
*   **Thermal & Environmental Limits:** As power consumption per rack rises, cooling high-density logic boards requires comprehensive direct liquid cooling infrastructure. This extends cold-plate requirements to peripheral components, including optical transceivers.
*   **Economic Viability of Multi-Die Packaging:** Achieving high memory bandwidth via multi-die chiplet designs (such as TPU 8i Max) requires advanced semiconductor packaging. System economic viability depends on maintaining high manufacturing yields as die sizes approach physical reticle limits.

---

## Key numbers

*   **7,800%+**: Year-over-year increase in autonomous agent-driven network traffic (Source: Google Cloud Tech, 2025).
*   **50% to 70%**: Share of total artificial intelligence compute consumption consumed by model inference, up from 40% two years prior.
*   **120 Quadrillion**: Projected global token demand per month by 2030 (a 24-fold increase in token demand and a 55-fold surge in required compute intensity).
*   **30x**: Matrix processing throughput advantage of the original TPU v1 over contemporary processors (2015).
*   **75 Watts**: Thermal design power rating of the original air-cooled TPU v1 PCIe accelerator card.
*   **9,600 chips**: Silicon scale of an 8th-generation TPU superpod, delivering 3x higher compute performance at 2.7x lower cost.
*   **19.2 Terabits per second**: Inter-chip interconnect bidirectional bandwidth per chip across the 8th-generation TPU copper ring.
*   **16 hops to 7 hops**: Reduction in worst-case network diameter achieved by the Board Fly mesh topology, cutting inter-chip latency by up to half.
*   **12.6 Petaflops**: Native FP4 compute capacity of a TPU 8TX system module.
*   **384GB**: High Bandwidth Memory capacity integrated into TPU 8i Max packages (a 33% increase over TPU 8i).
*   **17.2 Terabytes per second**: HBM memory bandwidth delivered by TPU 8i Max (double that of TPU 8i).
*   **768MB**: On-chip ultra-fast SRAM integrated onto TPU 8i Max silicon (double that of TPU 8i).
*   **1.09**: Trailing 12-month average fleet-wide Power Usage Effectiveness across Google Cloud data centers (83% less overhead energy than industry averages).
*   **30%**: Price-performance advantage of custom ARM-based Axion CPU instances compared to the next leading hyperscaler, supported by 40% higher network throughput via RDMA.

---

## What would change this picture

1.  **Widespread Adoption of CNCF Agent Substrate:** The velocity at which enterprise multi-cloud teams adopt Agent Substrate as an open Kubernetes standard versus adopting proprietary hyperscaler runtime sandboxes will determine cross-cloud agent portability.
2.  **Commercial Realization of Off-Grid Orbital Compute:** Demonstrating cost-competitive orbital processing during Project Suncatcher’s upcoming inter-satellite laser link tests will determine whether LEO space compute offers a practical alternative to terrestrial data center power grid constraints.
3.  **Shift in Accelerator Parity:** Real-world model execution benchmarks comparing native PyTorch on custom TPUs against next-generation GPU architectures (such as NVIDIA Vera Rubin and Blackwell) will dictate hardware procurement strategies for multi-tenant cloud environments.
4.  **Thermodynamic and Economic Packaging Limits:** Manufacturing yield rates for advanced multi-die packaging techniques—such as doubling compute dies within TPU 8i Max—will determine whether unit token economics can remain sustainable as physical reticle limits are reached.

---

To explore more open-source research and technical analyses, visit the DeepValues Research site or try the DeepValues app to evaluate enterprise AI infrastructure models.

---

## Sources

Google Cloud Tech, "The Future of AI Infrastructure" (featuring presentations by Amin Vahdat, Maria Biggs, and Mark Lohmeyer).
