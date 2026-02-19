# The Sovereign Intelligent Substrate: A First-Principles Redesign of the Operating System for the Agentic Era

The architecture of modern operating systems, while remarkably resilient over the past six decades, is currently facing a period of fundamental obsolescence. The foundational paradigms of computing-the Von Neumann architecture and the POSIX standard-were established during an era when hardware resources were scarce, workloads were deterministic, and the human user was the sole orchestrator of every discrete system action. As the digital landscape transitions into an era dominated by large-scale generative models, autonomous agents, and pervasive intelligence, the traditional operating system (OS) has become a bottleneck, a legacy shell struggling to contain a new form of computational energy. Designing a new operating system for the next several decades requires a radical departure from these heritage models, necessitating a shift from a process-oriented substrate to an intent-oriented substrate where intelligence is treated not as a feature, but as a primary utility of the kernel itself.

## The Structural Rot: Limitations of Legacy Architectures

The drawbacks of existing operating systems are not merely functional but architectural. Legacy systems were designed for predictable and deterministic workloads, which are fundamentally misaligned with the operational demands of modern artificial intelligence (AI) systems. These systems rely on monolithic or tightly coupled designs where application boundaries resist the flexibility required by AI workloads. In these environments, failures propagate easily across unrelated components, and iteration speed drops significantly because changes to models often require broader system releases. Furthermore, the lack of real-time processing capabilities in traditional OS kernels creates a disconnect with AI models that require continuous learning and near-instantaneous inference.

One of the most debilitating constraints of current systems is the existence of siloed and fragmented data stores. Traditional OS designs rely on multiple relational databases or hierarchical file systems optimized for specific applications, resulting in inconsistent feature definitions and high efforts for data cleansing. In most enterprise and consumer environments, 60% to 80% of IT budgets are consumed simply maintaining these outdated infrastructures, leaving minimal resources for innovation. These legacy systems also present significant security liabilities, as they lack modern security protocols for handling probabilistic outputs or protecting against prompt injection and sensitive data exposure.

| Constraint Category      | Legacy OS Characteristics               | Impact on AI Workloads                                                |
|--------------------------|-----------------------------------------|-----------------------------------------------------------------------|
| **Data Architecture**    | Siloed, inconsistent, and relational    | High latency in retrieval and poor data freshness for inference.      |
| **System Design**        | Monolithic and tightly coupled          | Rigid application boundaries that resist scaling and rapid iteration. |
| **Processing Pattern**   | Batch-oriented ETL and synchronous hops | Degraded user experience due to high inference latency.               |
| **Lifecycle Management** | Manual deployment and static monitoring | Absence of automated mechanisms for model drift and artifact updates. |
| **Security/Compliance**  | Rule-based and reactive                 | Inability to monitor dynamic risk thresholds or prevent model misuse. |

## First Principles of an AI-Native Operating System

To design a truly AI-native operating system, one must apply first-principles thinking to modern software constraints. In the coming decades, several truths will become objectively evident: intelligence will be abundant and cheap, computation will no longer be the primary bottleneck, and human attention and clarity will become the scarcest resources. If intelligence is a given utility, the fundamental design question for the OS changes from "how do we help users make better decisions?" to "which decisions should no longer exist?".

An AI-native system is defined by having intrinsic, trustworthy AI capabilities where AI is a natural part of design, deployment, operation, and maintenance. It is not merely a "wrapper" or a "copilot" layered on top of a legacy kernel; rather, AI operates at the core, shaping workflow design and system behavior. A simple test for an AI-native OS is whether removing the AI components causes the system to structurally fail. If the product still works without the intelligence layer, it is merely AI-enabled, not AI-native.

### The Evolution of the System Paradigm

The transition toward an AI-native OS follows a structured maturity curve. In the initial stage, augmented delivery, AI assists with discrete tasks like testing and documentation. As the system matures toward autonomous delivery, AI manages most delivery processes while humans retain strategic oversight. Finally, in the AI-native culture stage, the system achieves continuous evolution where every release is informed by self-learning pipelines. This requires moving from static pipelines to intelligent systems where AI agents act as collaborative teammates rather than mere tools.

## The Semantic Kernel: A New Vision for File Systems

The most profound change in the proposed OS architecture is the abandonment of the hierarchical file system in favor of a semantic memory hierarchy. Traditional file systems, which rely on rigid paths, directories, and filenames, are inherently unsuited for an era where agents must retrieve information based on context and meaning. In the new paradigm, the OS treats memory as knowledge, where files, actions, and data are semantically indexed and retrievable via natural language or goal-oriented queries.

### The Architecture of Semantic Storage

A semantic file system must be written as a kernel-level component to support the high-performance needs of semantic tagging and retrieval. This architecture employs a multi-level system that decomposes storage into layers with increasing abstraction. Lower tiers encode localized details, while higher tiers aggregate and index information at broader contextual levels, supporting task-adaptive information fusion. This stratification can be spatial, temporal, or semantic, ensuring that information is propagated and summarized across layers.

The kernel-native filesystem, such as the proposed VexFS or VectorVFS, stores vector embeddings directly alongside files, turning the directory structure into an efficient embedding store. This allows the system to support "cognitive git commits," where agents can snapshot their cognitive state, tied to contextual memory points in vector space. This architecture eliminates the need for external vector databases, providing a semantic memory layer that agents can mount natively.

| Memory Tier             | Abstraction Level | Mechanism                                                              |
|-------------------------|-------------------|------------------------------------------------------------------------|
| **Episodic Memory**     | Session-specific  | Conversation transcripts and tool outputs per session.                 |
| **Semantic Memory**     | Durable knowledge | High-dimensional vector embeddings of papers and documents.            |
| **Procedural Memory**   | Operational logic | Instructions and rules that shape agent behavior across sessions.      |
| **Hierarchical Memory** | Aggregate/Global  | Summary keys for fixed-length sequences enabling "mental time travel". |

### Content-Aware Storage and Security

To overcome the security challenges of semantic retrieval, the proposed system introduces Content-Aware Storage (CAS). CAS eliminates the need for separate access control lists (ACLs) for vectors by deeply integrating the vector database with the "system of record". It directly utilizes the ACLs defined in the storage system, ensuring that changes to file access are applied in real-time to the associated vectors. This deep integration ensures that security and data freshness are maintained without the need for periodic re-indexing or manual synchronization.

## The Agentic Scheduler: Orchestrating Task Execution

In an AI-native OS, task scheduling shifts from a process-oriented model to a goal-oriented model. Today's OS architecture is centered on multitasking between discrete applications; the AI-native OS focuses on orchestrated cognition, where the system coordinates agents and data to progress toward high-level goals. The scheduler no longer relies on ad hoc heuristics or fixed time quanta but employs predictive analytics and reinforcement learning to handle dynamic workloads.

### Learning-Based Scheduling Algorithms

Traditional scheduling, such as Round Robin (RR), often fails to account for varying process burst times, leading to inefficiencies. The new OS employs algorithms like Absolute Difference Based Time Quantum Round Robin (ADRR), which uses supervised learning (e.g., decision trees) to predict CPU burst times and adaptively select time quanta. Reinforcement learning models can further refine scheduling policies by analyzing historical task execution data and adjusting to changing system states in real time.

For highly parallel AI workloads, the OS must provide fine-grained isolation. The LithOS architecture introduces a TPC (Texture Processing Cluster) Scheduler that asynchronously determines compute unit allocation at the granularity of individual clusters. By atomizing monolithic kernels into small, schedulable subsets of thread blocks, the system can interleave work from different applications effectively, preventing long-running kernels from monopolizing the GPU. This "TPC Stealing" technique allows the system to reassign idle resources dynamically, guided by an online kernel latency predictor to avoid priority inversion.

### Capability-Centric Resource Management

A critical component of this new scheduling framework is the capability-centric interface. Instead of developers managing specific models or hardware runtimes, the OS provides a Virtual Capability Layer (VCL) with a unified API. This allows applications to call functions like generate(object\_detection) without needing to know the underlying XPU (GPU, NPU, or ASIC) or model format.

| API Category       | Functionality                   | System Impact                                                              |
|--------------------|---------------------------------|----------------------------------------------------------------------------|
| **Capability API** | Invokes high-level AI functions | Simplifies application code and abstracts hardware complexity.             |
| **Infer API**      | Manages execution lifecycle     | Allows for direct control over model loading/unloading for specific tasks. |
| **Manage API**     | Handles administrative tasks    | Facilitates collaborative resource management and model registry.          |

This unified service enables collaborative optimization, such as consolidating model instances across multiple concurrent applications, which can save up to 20 GB of disk space and 10 GB of memory on a typical device. Furthermore, by using "semantic hints"-indicating whether a task is a latency-sensitive one-shot task or a background batch process-the scheduler can perform dynamic device selection, offloading background tasks to power-efficient NPUs while reserving the GPU for foreground interactions.

## Generative User Interface: The End of Static Windows

The user interface of an AI-native OS represents a fundamental shift from direct manipulation to delegation. In the command-based paradigm of the last 60 years, users provided direct inputs to get direct results. The new paradigm, intent-based interaction, allows users to express a desired outcome while the system deduces the best method to achieve it. This marks the emergence of the Agentic Experience (AX), where the focus of design moves from static flows to the goals and capabilities of an agent acting on the user's behalf.

### Real-Time Interface Synthesis

Generative UI (GenUI) constructs, adapts, and optimizes interfaces in real-time based on user behavior and intent. Unlike traditional deterministic interfaces, GenUI is probabilistic; it analyzes context to predict which UI elements are necessary for a given task. For instance, a finance application might dynamically surface transaction indicators based on a user's history, or a telehealth platform might rearrange patient records to prioritize relevant history as a doctor mentions specific symptoms.

The interface effectively becomes "liquid," shaped by the ongoing relationship between the user and the agent. This requires the OS to handle multimodal inputs-voice, text, sketches, and gestures-interpreting them in natural context. In this model, the user is no longer managing tools but supervising a system that owns the context and memory of their workflows.

| Paradigm Feature   | Traditional GUI                             | Generative UI (GenUI)                             |
|--------------------|---------------------------------------------|---------------------------------------------------|
| **Logic Basis**    | Deterministic, predefined interaction trees | Probabilistic, inferred from intent and context.  |
| **Outcome Nature** | Fixed menus and one-size-fits-all flows     | Personalized, dynamic, and adaptive results.      |
| **User Role**      | Primary controller of discrete steps        | Strategy-focused supervisor and creative partner. |
| **Efficiency**     | Manual navigation through multiple screens  | One-shot or few-shot task completion.             |

\#\#\# Redefining Artificial Intelligence Experience (AIX)

Designing for intent-based systems requires a deep understanding of human relationship models. Because users articulate intent in ways that are inherently messy and contextual, the OS must incorporate behavioral science frameworks to build trust over time. The "interface" in this era is not just the visual output but the agent's ability to communicate progress and justify its decisions, making explainability a core system requirement.

## Cognitive Power Management and Heterogeneous Resource Allocation

The computational demands of edge AI neural network inference clash with the stringent power budgets of battery-operated devices. Traditional energy management relies on fixed schedules, which often lead to wasted power during idle periods or performance degradation during intensive matrix multiplications. An AI-native OS must employ cognitive power management, where AI dynamically adjusts resource allocation based on real-time activity and environmental state.

### Dynamic Scaling and Thermal Efficiency

The integration of Neural Processing Units (NPUs) is critical for accelerating AI inference at low power. However, mobile SoCs often feature a unified memory architecture (UMA) where CPU, GPU, and NPU share the same address space. To maximize performance, the OS must manage heterogeneous parallel mechanisms. For example, while a single GPU might only utilize 40-45 GB/s of memory bandwidth, concurrently employing an NPU can achieve up to 60 GB/s, significantly improving LLM inference speeds.

The proposed OS uses predictive analytics to forecast workload peaks, allowing it to scale resources up or down automatically. In industrial settings, this intelligent automation has demonstrated the potential to reduce energy use by up to 10% through smarter process control. On a consumer device, this translates to an OS that can "sleep" between inference cycles without breaking timing requirements, using reinforcement learning to optimize inverter behavior and storage coordination.

### NPU Virtualization and vNPU Abstractions

To address the underutilization of AI accelerators, the OS must move away from the current model of assigning an entire NPU chip to a single application. The Neu10 framework proposes a "vNPU" abstraction that enables fine-grained virtualization of heterogeneous compute units (e.g., matrix engines and vector engines). This allows for a "pay-as-you-go" computing model where workloads with diverse resource requirements can share physical hardware efficiently through dynamic scheduling of micro-tensor operators.

## Sovereign Privacy and the Personal Data Vault

As the operating system becomes a "thinking partner" with access to sensitive medical, financial, and personal logs, the traditional opt-out model of data privacy is no longer tenable. The new OS architecture is built upon the concept of a Personal Data Store (PDS) or "Personal Data Vault," where all personal data is private by default and owned entirely by the individual rather than a corporate entity.

### The Decentralized Data Dominion

The Personal Data Vault acts as a user-governed repository that separates data storage from service providers. By enabling individuals to consolidate data from social media history, health records, and banking patterns into a single digital wallet, the OS empowers them to grant or revoke third-party access at any time. This decentralized approach not only enhances privacy but also enables new AI-powered "digital twins" that can interact with the user's data on their behalf.

### Differential Privacy at the Kernel Level

To protect the integrity of the data used for model training and personalization, the OS integrates differential privacy (DP) as a system-level primitive. DP provides rigorous mathematical guarantees that the output of an algorithm does not reveal the presence of any single individual's data. This is particularly important for user-level differential privacy, which is a stronger form of protection than example-level DP, as it makes it impossible to tell if *all* of a user's data was included in a training set.

The OS defines a strict trust boundary consisting of the user's device and a Trusted Execution Environment (TEE). Any information leaving this boundary is protected by noise injection (e.g., DP-SGD). Furthermore, techniques like homomorphic encryption allow computations to occur on encrypted data without decryption, preserving privacy even during intensive analysis.

| Privacy Guardrail        | Mechanism                                    | Purpose                                                                             |
|--------------------------|----------------------------------------------|-------------------------------------------------------------------------------------|
| **Data Redaction**       | Automated scanning of prompts and embeddings | Identifies and masks PII before it reaches models.                                  |
| **Tokenization**         | deterministic stand-ins for sensitive data   | Prevents plaintext sensitive data from flowing into LLMs while allowing processing. |
| **Differential Privacy** | Calibrated noise injection (DP-SGD)          | Bounds the influence of individual data points on model outputs.                    |
| **Personal Data Vault**  | Decentralized PDS architecture               | Ensures user ownership and granular consent for data usage.                         |
| **Access Control**       | RBAC and ABAC for AI agents                  | Treats agents as privileged identities with least-privilege principles.             |

## First-Principles Design of System Interfaces: Intent-Based System Calls

The traditional System Call (syscall) interface, designed to provide a secure gateway to kernel services like file I/O or networking, must be reimagined. In an AI-native OS, programming becomes equivalent to specifying workflows through instructions or prompts. The "System Call 2.0" is an intent-based abstraction that encodes functional and operational requirements at a high level.

### The Three Stages of Intent Fulfillment

An Intent-Based System (IBS) processes requests through a closed-loop automation cycle:

1.  **Intent Ingestion**: Natural language or multimodal inputs are recognized and collected through user interactions, often mediated by dialogue assistants.

2.  **Intent Translation**: High-level goals are interpreted and converted into machine-readable formats, decomposing the intent into specific commands or configurations.

3.  **Intent Assurance**: The system continuously monitors its own performance to verify compliance with the intent, refining its behavior to maintain the desired quality of service.

This architecture allows the system to autonomously synthesize human intents into working software-essentially moving from an "idea" to a functional system without manual user involvement in the underlying implementation. This "Compiler-next" approach leverages foundational models to iteratively develop solutions at high speed through code mutations and self-reflection.

## The Road Ahead: 2030 and Beyond

The transition to an AI-native operating system is not merely a technological upgrade but a fundamental shift in how humanity relates to digital information. As we move toward 2030 and beyond, several speculative but grounded developments are expected:

-   **2025-2026**: Breakthroughs in distributed architectures and deeper integration between AI frameworks and vector databases.

-   **2027**: Maturation of vector databases integrated with knowledge graphs to support high-order reasoning.

-   **2030**: The arrival of "superintelligence" environments where traditional UI design vanishes in favor of liquid agentic experiences.

The ultimate goal of this first-principles redesign is to create a system that is no longer a passive tool but a "sovereign intelligent substrate." This OS will act as an external brain-reminding users what a contractor said about tiles, summarizing three months of health logs, and planning entire conferences based on a single voice prompt. By reclaiming data ownership through Personal Data Vaults and orchestrating hardware through predictive, intent-aware kernels, we lay the foundation for a future where technology truly serves the human condition, rather than the other way around.

# LinkedIn Version: The Death of the OS as We Know It 🚀

We've been living in the "Command Paradigm" for 60 years. We click, we drag, we open files. We are the orchestrators; the OS is just a passive shell.

But that shell is breaking.

I just finished a deep-dive research report on the first-principles design of an **AI-Native Operating System**. If we stop layering AI on top of legacy systems and start building from the kernel up, what changes? Everything.

📁 **The Hierarchical File System is Dead.** Folders are for humans, not intelligence. The new OS uses a "Semantic File System" where memory is knowledge. You don't find "Project\_v2.doc"; you ask for "that analysis about the Norway AI fund from last April." It's retrievable because it has meaning, not a path.

⚙️ **The End of Fixed Scheduling.** Traditional OSs use Round Robin. The AI-Native OS uses "Predictive Scheduling." It analyzes your habits to allocate GPU and NPU resources *before* you even trigger the task. It atomizes kernels into "atoms" to ensure no single process can hog your intelligence.

🎨 **Liquid UI (AX &gt; UX).** Forget static windows. We're moving to "Generative UI." The interface builds itself in real-time based on your intent. If you're a doctor, the records you need surface automatically. If you're a designer, the tools adapt to your sketch. We are moving from "User Experience" to "Agentic Experience."

🛡️ **Sovereign Privacy.** Your data doesn't belong to the cloud. It lives in your "Personal Data Vault." All system-level personalization happens through Differential Privacy and Secure Enclaves. You don't "opt-out" of data collection; you "opt-in" to specific services using your private vault.

The OS is no longer a tool; it's a teammate.

Are we ready for an OS that understands us better than we understand ourselves? Read the full thesis below to see the roadmap for the next three decades of computing.

\#AI \#OperatingSystems \#TechVision \#AgenticAI \#Privacy \#FutureOfTech \#ProductDesign \#ComputerScience

# Hot Title: The Intent-Based Substrate: Designing a Sovereign AI-Native Operating System for the Next Half-Century

#### Works cited

1\. AI-Native Is First-Principles Thinking, Not a Feature Upgrade - Software Co, https://www.softwareco.com/ai-native-is-first-principles-thinking-not-a-feature-upgrade/ 2. Defining AI native: A key enabler for advanced intelligent telecom networks - Ericsson, https://www.ericsson.com/en/reports-and-papers/white-papers/ai-native 3. Integrating Artificial Intelligence into Operating Systems: A Survey on Techniques, Applications, and Future Directions - arXiv, https://arxiv.org/html/2407.14567v3 4. AI-Driven Operating Systems - Emergent Mind, https://www.emergentmind.com/topics/ai-driven-operating-systems 5. AI Implementation Challenges: Why Legacy Architectures Break Modern AI Workloads, https://www.arielsoftwares.com/ai-implementation-challenges-legacy-architecture/ 6. Challenges of Integrating Artificial Intelligence in Legacy Systems and Potential Solutions for Seamless Integration, https://nebula.wsimg.com/d9df7fd1c12b112332040e6abaf803db?AccessKeyId=809C1E9E538F4C38BEAB&disposition=0&alloworigin=1 7. Architectural challenges in modernizing legacy financial systems with microservices and AI - World Journal of Advanced Engineering Technology and Sciences, https://wjaets.com/sites/default/files/fulltext\_pdf/WJAETS-2025-0651.pdf 8. Why Legacy Modernization Is No Longer Optional in the Age of AI & Cloud, https://www.200oksolutions.com/blog/why-legacy-modernization-is-no-longer-optional-in-the-age-of-ai-cloud 9. AI data privacy: guardrails that protect sensitive data - F5, https://www.f5.com/company/blog/ai-data-privacy-guardrails-that-protect-sensitive-data 10. What does "AI-native development" actually mean? - First Line Software, https://firstlinesoftware.com/blog/what-does-ai-native-development-actually-mean/ 11. AI-Native Software Engineering: Building Intelligent, Autonomous, and Governed Delivery Pipelines - UST, https://www.ust.com/en/insights/ai-native-software-engineering-intelligent-delivery 12. The AI-Native OS: Rethinking the Operating System from First Principles \| by Yashash Gc, https://medium.com/@yashash.gc/the-ai-native-os-rethinking-the-operating-system-from-first-principles-a2b5c02332a6 13. Show HN: VexFS - A Kernel-Native Semantic Filesystem for AI Agents - Hacker News, https://news.ycombinator.com/item?id=44095926 14. Hierarchical Memory Architecture - Emergent Mind, https://www.emergentmind.com/topics/hierarchical-memory-architecture 15. Semantic File Systems - A Filesystem Geek, https://fsgeek.ca/my-research/semantic-file-systems/ 16. VectorVFS: your filesystem as a vector database - OSnews, https://www.osnews.com/story/142293/vectorvfs-your-filesystem-as-a-vector-database/ 17. Content aware storage for the generative AI era - IBM Research, https://research.ibm.com/blog/content-aware-storage-generative-ai 18. leveraging ai and ml for predictive scheduling in real-time operating systems, https://www.researchgate.net/publication/387958272\_LEVERAGING\_AI\_AND\_ML\_FOR\_PREDICTIVE\_SCHEDULING\_IN\_REAL-TIME\_OPERATING\_SYSTEMS 19. Sentient OS : AI-Enhanced CPU Scheduling in Modern Operating Systems - ijarsct, https://ijarsct.co.in/Paper29824.pdf 20. LithOS: An Operating Systemfor Efficient ... - Parallel Data Lab, https://www.pdl.cmu.edu/PDL-FTP/BigLearning/lithos\_sosp25.pdf 21. A System-level Abstraction and Service for Flourishing AI ... - ipads-sjtu, https://ipads.se.sjtu.edu.cn/\_media/publications/xserv-apsys25.pdf 22. The Future of Interaction: Generative AI and the Evolution of UX - MindPort, https://www.mindport.ca/insights/the-future-of-interaction-generative-ai-and-the-evolution-of-ux 23. The End of the User Interface?. The AI Agent Revolution and the ..., https://uxplanet.org/the-end-of-the-user-interface-31a787c3ae94 24. Human-Centered AI Design: Creating Intent-Based Experiences - Tietoevry, https://www.tietoevry.com/en/blog/2025/10/designing-for-ai-world/ 25. Generative UI: The AI-Powered Future of User Interfaces \| by Khyati Brahmbhatt \| Medium, https://medium.com/@knbrahmbhatt\_4883/generative-ui-the-ai-powered-future-of-user-interfaces-920074f32f33 26. Generated User Interfaces (GenUIn) \| Blog des Fraunhofer IOSB, https://blog.iosb.fraunhofer.de/generated-user-interfaces-genuin/ 27. Low-latency power management in edge AI architectures - Avnet, https://www.avnet.com/integrated/resources/article/low-latency-power-management-in-edge-ai-architectures/ 28. AI and Machine Learning in Industrial Power Management - EEPower, https://eepower.com/industry-articles/ai-and-machine-learning-in-industrial-power-management/ 29. AIOps - Agentic AI for IT Operations and Management - XenonStack, https://www.xenonstack.com/blog/aiops-it-operations-management 30. Unlocking on-device generative AI with an NPU and heterogeneous computing \| Qualcomm, https://www.qualcomm.com/content/dam/qcomm-martech/dm-assets/documents/Unlocking-on-device-generative-AI-with-an-NPU-and-heterogeneous-computing.pdf 31. Characterizing Mobile SoC for Accelerating Heterogeneous LLM Inference - arXiv, https://arxiv.org/html/2501.14794v2 32. AI-Driven Scheduling For Predictive Analytics - Meegle, https://www.meegle.com/en\_us/topics/intelligent-scheduling/ai-driven-scheduling-for-predictive-analytics 33. Hardware-Assisted Virtualization of Neural Processing Units for Cloud Platforms - Illinois PlatformX, https://platformxlab.github.io/papers/neu10-micro24.pdf 34. Full article: Understanding User Perceptions of Personal Data Stores: A Prototype-Driven Multi-Scenario Study - Taylor & Francis, https://www.tandfonline.com/doi/full/10.1080/10447318.2025.2545467 35. Dr Paulius Jurčys: A New Social Contract. Reclaiming Ownership of Our Data - Vilniaus universitetas, https://www.vu.lt/en/news-events/news/dr-paulius-jurcys-a-new-social-contract-reclaiming-ownership-of-our-data 36. A Systematic Review on Privacy-Aware IoT Personal Data Stores - PMC, https://pmc.ncbi.nlm.nih.gov/articles/PMC11014407/ 37. Differential privacy semantics for On-Device Personalization, https://privacysandbox.google.com/protections/on-device-personalization/differential-privacy-semantics-for-odp 38. Differential Privacy in ML: Protecting Sensitive Data in AI Systems - ResearchGate, https://www.researchgate.net/publication/390131522\_Differential\_Privacy\_in\_ML\_Protecting\_Sensitive\_Data\_in\_AI\_Systems 39. A Comprehensive Guide to Differential Privacy: From Theory to User Expectations - arXiv, https://arxiv.org/html/2509.03294v1 40. Fine-tuning LLMs with user-level differential privacy - Google Research, https://research.google/blog/fine-tuning-llms-with-user-level-differential-privacy/ 41. Framework for Data Protection, Security, and Privacy in AI Applications 1 Introduction 2 Contextual Background, https://www.nist.gov/document/ai-eo-14110-rfi-comments-loughborough-university 42. (PDF) Intent-based System Design and Operation - ResearchGate, https://www.researchgate.net/publication/388883547\_Intent-based\_System\_Design\_and\_Operation 43. Intent-Based Infrastructure and Service Orchestration Using Agentic-AI - IEEE Xplore, https://ieeexplore.ieee.org/iel8/8782661/10829557/11131150.pdf 44. Intent-Based Management for Open RAN: Intelligent Network Configuration Automation via Chatbot - ResearchGate, https://www.researchgate.net/publication/387597913\_Intent-Based\_Management\_for\_Open\_RAN\_Intelligent\_Network\_Configuration\_Automation\_via\_Chatbot 45. A Search-Based Compiler to Power the AI-Native Future of Software Engineering - arXiv, https://arxiv.org/html/2510.24799v1 46. (PDF) Introduction to Vector Databases for Generative AI: Applications, Performance,Future Projections, and Cost Considerations - ResearchGate, https://www.researchgate.net/publication/389362484\_Introduction\_to\_Vector\_Databases\_for\_Generative\_AI\_Applications\_PerformanceFuture\_Projections\_and\_Cost\_Considerations
