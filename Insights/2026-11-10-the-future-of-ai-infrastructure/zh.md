---
title: "從太空實驗到 Agent 算力革命：Google 第八代 TPU 家族與 AI 基礎設施重構解析"
date: "2026-11-10"
lang: "zh"
category: "ai"
tickers: []
notebook_id: "6d8f2e3d-1ef8-4b35-a56f-12853b2c3614"
source_urls:
  - title: "The Future of AI Infrastructure"
    url: "https://www.youtube.com/watch?v=pabDkNR7jIs"
youtube: []
podcast: []
generated_by: "NotebookLM + DeepValues editors"
disclosure: "AI-assisted"
---

# 從太空實驗到 Agent 算力革命：Google 第八代 TPU 家族與 AI 基礎設施重構解析

本篇深度分析文章探討 Google 最新發布的第八代 TPU 家族晶片架構、AI Hypercomputer 全棧協同設計（Co-design）、Agent Compute Engine 執行環境以及前瞻的 Project Suncatcher 低軌衛星算力實驗。隨著人工智慧流量正經歷從人類對話轉向自主代理（Agent）運作的根本性變革，推論（Inference）算力消耗已躍升至全球 AI 總算力的 50% 至 70%。面對 Agent 時代帶來的記憶體牆（Memory Wall）、網路傳輸延遲與安全隔離等嚴峻瓶頸，Google 透過硬體與軟體的深度協同設計，發表了 TPU 8i、TPU 8X、TPU 8 Max 等專用晶片組態與 Agent Compute Engine。此一基礎設施重構有效解決了代理架構的效能瓶頸與安全風險，建立起高能效且具備經濟永續性的 AI 算力架構，為企業規模化部署 Agent 生態系提供堅實的底層支撐。

---

## 1. 概念與起源：從 Voice Search 瓶頸到 Agent 時代的三維轉型

Google 構建超大型運算基礎設施的起點，可以追溯至 25 年前在瓦楞紙板與通用晶片上組裝的第一個貨櫃式資料中心。當時工程團隊抱持著一項前瞻信念：透過軟體調度數千台普通機器，即可發揮等同於超級電腦的運算威力，進而奠定了網頁搜尋引擎與現代雲端運算（Cloud Computing）的根基。

然而，真正促使 Google 走向自研特定領域處理器（Domain-Specific Processor）的轉折點，發生在 2013 年的一次算力危機。當時工程團隊嘗試在 Google Voice Search（語音搜尋）服務中部署早期神經網路模型，隨即進行了嚴密的第一性原理算力推演：若全球每位 Android 使用者每天僅使用 3 分鐘的語音搜尋，其產生的矩陣運算需求，將逼迫 Google 將全球現有的資料中心規模翻倍建置。

這種實體與經濟層面的不可能性，促使 Google 拋棄傳統通用 CPU/GPU 的設計思維，轉而針對神經網路的核心語言——矩陣數學（Matrix Mathematics）——設計專用加速器。這項決定促成了 2015 年第一代張量處理器（Tensor Processing Unit, TPU v1）的誕生，當時即展現出較同世代處理器高出 30 倍的吞吐量表現。

十年後的今天，全球 AI 工作負載正經歷一場更加劇烈的根本性轉型。根據 Amin Vahdat 在演講中指出：「當您在 Google Search 輸入查詢時，它會在幾百毫秒內協調跨 10,000 台伺服器。」然而，隨著 Gemini 等模型演進為通用 AI Agent，AI 的互動模式與基礎設施需求已經發生了實質的改變。過去一年中，由 Agent 驅動的網路流量暴增了超過 7,800%；推論占整體 AI 算力消耗的比重，也從兩年前的 40% 急速上升至現今的 50% 至 70%。

這標誌著 AI 基礎設施正在面臨「三維轉型（Three Dimensions）」：
1. **從人類規模（Human Scale）轉移至 Agent 規模（Agent Scale）**：運算主體從數億人類使用者擴展至數百億個自主運作的 Agent。
2. **從紀錄系統（Systems of Record）轉移至行動系統（Systems of Action）**：AI 不再僅用於查詢與檢索資料，而是直接授權執行實質行動與任務。
3. **從單次簡單請求（Simple Requests）轉移至複雜 Agent 工作流程（Complex Agentic Workflows）**：工作負載從單回合的問答轉變為長跨度的多步驟推理。

在算力需求上，人類互動與 Agent 執行任務存在著本質上的巨大差異。當人類與 AI 互動時，通常僅是在短暫的往復對話中消耗約 1,000 個 Token（語意標記單元，模型處理文字與符號的基本單位）；然而，當 Agent 接收到一個宏觀目標時，它會自行拆解目標、撰寫程式碼、查詢模型、調用外部工具、檢查輸出結果並進行自我修正。這種運算機制將單次推論轉化為持續運行的閉環（Ongoing Loop），過程中會觸發數十個子代理（Subagents）、發動數百次模型查詢，並在跨越數日的任務中消耗數百萬個 Token。

根據行業預測，全球 Token 需求預計在 2030 年前將增長 24 倍，達到每月超過 120 Quadrillion（12 億億）個 Token。為了讓現代 AI 在商業上具備經濟可行性，基礎設施的算力強度必須實現 55 倍的飛躍提升，這迫使資料中心設施、算力配置、網路架構、資料儲存、晶片運行時（Runtime）與軟體框架必須進行從零開始的全棧重構。

---

## 2. 第一性原理硬體解構：TPU 的六大設計原則與低軌衛星實驗

為了解決傳統硬體的效能瓶頸，Google TPU 架構從底層即遵循六大第一性原理設計原則：

1. **軟體編譯器控制（Compiler-Controlled Execution）**：捨棄傳統硬體複雜的執行緒排程器（Thread Schedulers）與動態分歧邏輯（Dynamic Branching Logic），採用數量較少但面積較大的核心，將執行指令的精確排程完全交由軟體編譯器規劃。
2. **脈動陣列（Systolic Arrays）**：採用資料流架構。若將傳統 CPU 比喻為每次運算都要回記憶體「抓取資料」，脈動陣列則像是一個實體的乘法器網格，資料在網格節點之間持續流動並在週期運算中重複利用（Cycle-after-cycle Reuse），無需在每次操作時頻繁存取暫存器。
3. **編譯器控制記憶體（Compiler-Controlled Memory）**：取消傳統硬體的自動快取機制（Hardware Caches），完全由編譯器精確調度資料移動的時間點，進而消弭記憶體存取帶來的延遲突波（Latency Spikes）。
4. **光學電路交換器（Optical Circuit Switches, OCS）**：使用微型鏡片反射光束來直接連接數千顆 TPU 晶片，避免了傳統電子交換器（Electrical Switches）的高功耗與封包高遺失率問題。
5. **精簡數字格式（Compact Number Formats）**：優先考量數值範圍而非過度冗餘的精度，率先導入 bfloat16 與 Native FP4（4 位元浮點數），在維持嚴格位元確定性（Bitwise Determinism）的前提下，極大化每瓦能量所能執行的數學運算量。
6. **水冷冷卻板（Liquid Cooling Cold Plates）**：液體冷卻板直接緊貼矽晶片封裝，解決高密度運算產生的熱量，確保晶片能長時間維持在峰值時脈運行。

在實體硬體的進化上，2015 年推出的第一代 TPU v1 僅是一張功耗 75 瓦、採用風冷散熱的 PCIe 卡，由工程團隊在 15 個月內快速開發完成。相對地，最新的第八代 TPU 板卡托盤展示了極致的半導體工程：
板卡中央整合了雙晶片多模組封裝（Multi-Die Packages），板卡內部疊加了重型銅製供電層（Heavy Copper Power Planes），能在緊鄰矽晶片的位置進行直接降壓，消除電力傳輸的瓶頸。每顆晶片兩側配備了 6 個 HBM3E 高頻寬記憶體堆疊（整張板卡共 12 個 HBM3E 堆疊）。在晶片間通訊方面，採用了新一代晶片間互連（Inter-chip Interconnect, ICI）技術，透過板底的多維度銅環結構，提供單晶片每秒 19.2 Terabits（19.2 Tbps）的雙向頻寬。此外，為了因應極致的算力密度，光學電路交換器的光收發器（Optical Transceivers）本身也首度加裝了銅製水冷板組合——在如此高的功耗密度下，連光束傳送介面都必須依賴液體冷卻。

除了地面的極限工程，Google 更透過「Project Suncatcher」創新計畫探討未來的太空算力部署。根據 Maria Biggs 在演講中指出：「將這個大膽的想法轉化為切實可行的現實，需要進行律己且循序漸進的實驗。」

Google 將原型衛星部署至低地球軌道（LEO），探索利用太空環境中接近恆定的太陽能來驅動機器學習工作負載的可行性。計畫團隊已成功與衛星建立通訊，並完成太空「Hello World」測試：從地面傳送 Prompt（提示詞）至軌道衛星，由衛星上的 TPU 完成模型推論後，再將結果回傳至地面驗證。該實驗正在收集硬體在宇宙輻射、發射震動以及真空熱管理等極端環境下的第一手數據，並規劃於明年發射雙衛星系統，進一步測試星際雷射鏈路（Intersatellite Laser Links）的光學網路傳輸。

---

## 3. 第八代 TPU 家族：針對推論與 Agent 瓶頸的專用架構

第八代 TPU 家族針對不同的 AI 工作負載階段，劃分為四種專用架構組態：

### 3.1 TPU Superpod (Training)
專為前沿大模型訓練設計，單一 Superpod 可擴展至 9,600 顆晶片，提供前代產品近 3 倍的運算效能，能將複雜大模型的訓練時間從數月縮短至數週，同時將訓練成本降低 2.7 倍。

### 3.2 TPU 8i (Inference)
專為低延遲即時推論打造。傳統訓練採用 3D Torus（三維環形）網路拓撲，在環形相鄰晶片間逐跳傳送資料（Hopping），最差情況下需經歷 16 次中繼跳躍（16 hops）。這在 Agent 進行推論、需針對每個生成 Token 協調跨晶片部分和（Partial Sums）時，會造成延遲累積與回應卡頓。TPU 8i 導入了全新的 Boardfly 網路拓撲——一種階層式的低直徑網格結構（Hierarchical Low-Diameter Mesh），提供跨板卡與機架的直接高速捷徑，將最壞情況下的網路直徑從 16 hops 大幅降至 7 hops，減少高達 50% 的晶片間通訊延遲。此外，TPU 8i 將 HBM 記憶體擴充 50% 至 288GB，提供 8.6 TB/s 記憶體頻寬，並在晶片上整合 3 倍容量的 SRAM 快取，為低延遲服務提供高達 80% 的每美元效能提升。

### 3.3 TPU 8X (Confidential & RL)
為解決「企業信任」與「強化學習（RL）瓶頸」而設計。受到嚴格管制產業的企業需要硬體層級的資料加密，而 AI 開發者則需要能在同一晶片上同時運行推論與強化學習。TPU 8X 結合客製化 AMD 主機處理器，提供 12.6 Petaflops 的 Native FP4 算力與 216GB HBM。其透過硬體層級的 PCIe 鏈路加密、密碼學證明（Cryptographic Attestation）與安全記憶體安全區（Secure Memory Enclaves），實現矽晶片根源的機密運算（Confidential Computing），並採用與 AI 相同的 low-latency 網路，使通訊延遲較前代降低一半。

### 3.4 TPU 8 Max (Massive Context)
專為突破「大規模上下文」與「高併發 Agent 密度瓶頸」設計。當 Agent 在數百萬 Token 的長上下文環境中進行推理並以集群（Swarms）併發運作時，記憶體頻寬會成為主要瓶頸。TPU 8 Max 採用雙晶片單封裝設計（Dual Compute Dies in a Single Package），將每封裝的 HBM 記憶體容量提升至 384GB（較 8i 增加 33%），HBM 記憶體頻寬達到驚人的 17.2 TB/s（為 8i 的 2 倍），片上 SRAM 更翻倍至 768MB，並提供 2 倍的 FP4 算力。

Amin Vahdat 使用了公路拓寬的比喻來解釋 TPU 8 Max 的設計哲學：這就像是拓寬高速公路——目的不是讓單一車輛開得更快（單一 Token 生成速度保持極速），而是增加更多車道以消除交通堵塞。透過將記憶體頻寬翻倍至 17.2 TB/s，系統能夠允許大量併發的 Agent 同時存取與生成 Token，維持高密度運算而不觸及記憶體牆。

### 第八代 TPU 家族主要晶片組態對比表

| 晶片系統名稱 | HBM 記憶體容量 / 頻寬 | 核心特色與架構優勢 | 主要應用場景 |
| :--- | :--- | :--- | :--- |
| **TPU 8i** | 288GB / 8.6 TB/s | Boardfly 拓撲（直徑降至 7 hops）、SRAM 擴展 3 倍、降低跨晶片通訊延遲 50% | 低延遲即時推論與回應 |
| **TPU 8X** | 216GB / 8.6 TB/s | 結合 AMD 主機、硬體級 PCIe 加密、安全記憶體安全區、密碼證明 | 機密運算與強化學習（RL） |
| **TPU 8 Max** | 384GB / 17.2 TB/s | 雙晶片單封裝設計、768MB 片上 SRAM、2 倍 FP4 算力與 HBM 頻寬 | 大規模上下文與高併發 Agent 集群 |

---

## 4. 軟體全棧開放與 Agent Compute Engine 執行環境

硬體創新必須搭配開放的軟體生態才能發揮最大價值。根據 Mark Lohmeyer 在演講中指出：「我們的策略絕非建立單一途徑，您需要有自由選擇多種加速器平台而不必在效能上妥協。」

### 4.1 開放軟體堆疊與解構式服務（Disaggregated Serving）
* **PyTorch 原生支援（torch TPU）**：Google 與 Meta 的 PyTorch 團隊合作推出 `torch TPU`，使 TPU 成為 PyTorch 的原生後端。開發團隊無需重寫既有的 PyTorch 模型程式碼，即可直接在 TPU 上運行。
* **開源推論引擎原生整合**：與 Ecosystem 夥伴（Interact 及 Radix Arc）合作，使 TPU 出廠即原生支援 vLLM 與 SGLang 推論引擎。
* **多元加速器雙軌策略**：除了 TPU 之外，Google Cloud 亦持續提供最新的 NVIDIA 算力。例如在 AI Hypercomputer 上提供基於 NVIDIA Vera Rubin 架構的 A5 實例；並透過 Google Distributed Cloud（GDC）結合 NVIDIA Blackwell 平台，支援絕緣隔離環境（Air-gapped）下的 Sovereign（主權 AI）工作負載。
* **TPU Sync 記憶體卸載**：當 Agent 在等待外部 API 回覆或人工審查（Human-in-the-loop）而暫停運算時，TPU Sync 能立即將晶片上的工作記憶體移至伺服器主記憶體，待下一步推理開始時再快速流回，避免晶片閒置浪費。
* **LMDB 1.0 與 GKE 推論網關的解構式服務**：在傳統推論中，人類提示詞短而輸出長；然而 Agent 的輸入上下文極為巨大（包含系統指令、工具定義與歷史對話），若將「提示讀取（Prefill）」與「Token 生成（Decode）」放在同一顆晶片運行，兩者會劇烈爭奪晶片資源。Google 作為開源推論控制平面 LMDB 的創始貢獻者，已將其升級至 1.0 版本並整合至 Google Kubernetes Engine (GKE) Inference Gateway。LMDB 透過前綴快取感知路由（Prefix Cache-Aware Routing）與三層 Key-Value (KV) 快取卸載機制（記憶體、主機 CPU、持久化儲存），實現了**解構式服務（Disaggregated Serving）**——將 Prefill 與 Decode 拆分為獨立的算力池，在混合加速器集群間維持長脈絡快取，並提供多租戶服務品質（QoS）隔離。

### 4.2 Agent Compute Engine 專用執行環境
為了滿足 Agent 運作的三大底層需求——多層安全隔離、即時啟動（Instant Activation）以及狀態保持（Statefulness），Google 研發了全新的 Agent Compute Engine 運算基礎設施。

Agent Compute Engine 具備三大安全隔離層級：
1. **核心層（Kernel Level）**：每個 Sandbox（沙盒）皆運行於 Cloud Hypervisor 微型虛擬機（MicroVM）上，擁有獨立的 Guest Kernel，與宿主機完全隔離。
2. **網路層（Network Level）**：整合 Agent Gateway，從 MicroVM 外部強制執行精確的出站策略（Egress Policies）與網域白名單。
3. **身分層（Identity Level）**：MicroVM 環境內嚴禁硬體編碼憑證（Zero Hardcoded Credentials），改由外部動態注入密碼學驗證的身分標籤。

在狀態保持與效能方面，Agent Compute Engine 支援 root 存取權限、Hyperdisk 區塊儲存與 GCS Fused 目錄掛載。當 Agent 進入等待狀態時，系統會自動暫停 MicroVM 並完整捕獲記憶體與磁碟狀態；當收到觸發信號時，能夠無縫復原（Resume），使單一宿主機可支援高密度運行數千個 MicroVM。此外，該架構結合 Titanium 基礎設施處理器（Infrastructure Processing Unit, IPU），將網路、儲存與線路速率加密（Line-rate Encryption）卸載至專用矽晶片上，並由記憶體安全的 Rust Hypervisor 管理，從根本上杜絕記憶體損壞與沙盒逃逸漏洞。

### 4.3 雙重部署路徑、社群治理與開源捐贈
針對企業部署 Agent Compute Engine，Google 提供兩條明確的戰略路徑選擇：
* **託管式 API 方案（Managed API）**：適合追求極速上線與零維運負擔的團隊，可直接透過 API 開啟、暫停或刪除 MicroVM 沙盒，獲得全託管的即時擴展能力。
* **開源 Agent Substrate 方案**：適合重視高度客製化與跨雲遷移自由度（Multi-cloud Portability）的企業。團隊可在原有的 GKE 或地端 Kubernetes 集群上調度 Agent 沙盒。

為避免 Agent 時代的底層架構走向封閉，Google 宣布將內部的 Agent 執行環境開源專案——**Agent Substrate**——正式捐贈給雲端原生計算基金會（CNCF）。開發者可透過標準 Kubernetes API 調度 Agent 沙盒。此外，Google 亦構建了統一的 Agent 治理模型，包含負責流量調度的 Agent Gateway、管理工具目錄的 Agent Registry、提供數位簽章的 Agent Identity，以及捕捉全棧電信數據的 Agent Observability，確保跨雲與地端環境的統一治理。

---

## 5. 商業經濟學、能效優勢與產業影響

Agent 工作流程的普及顯現了著名的「焦文斯悖論（Jevons Paradox）」：當智力產生成本（Cost of Intelligence）顯著降低時，企業對算力的總需求並未減少，反而因單位成本下降而誘發了大規模的新增需求——企業開始將簡單的單次查詢擴展為連續運作的多 Agent 自動化工作流程。

為了在經濟上支撐這種爆炸性的算力需求，基礎設施的能效成為決定性的商業變數。Google 資料中心在過去 12 個月中實現了 Fleet-wide（全機隊）平均 1.09 的電力使用效率（PUE），這意味著其資料中心營運產生的額外能源消耗比業界平均水準低了 83%。結合晶片與模型層面的共同優化，Google 資料中心目前每單位能量所提供的算力效能，已較 5 年前提升了 3 倍以上。

此外，在 CPU 層面，Google 自研的 ARM 架構處理器 Axion 配合高效能 RDMA 網路，提供了較下一代主要雲端業者高出 30% 的每美元效能優勢與 40% 的吞吐量提升。

這種全棧協同設計（Co-design）帶來的經濟效能，大幅降低了 Token 產生成本。全球大型企業（如金融服務、醫療照護、電信業）以及數位原生企業（Digital Natives），得以在具備商業永續性的成本架構下，將前沿 Agent 系統大規模部署至實體生產環境中。

---

## 6. 架構限制與尚未解決的挑戰

雖然第八代 TPU 家族與全棧 AI 基礎設施展現了突破性的技術指標，但在實際物理維度與工程落地層面，仍存在以下客觀限制與待解挑戰（包含資料證實內容與合理技術推論）：

1. **光學與散熱工程的物理極限（資料證實）**：儘管光學電路交換器（OCS）大幅降低了傳輸功耗，但光訊號收發器（Optical Transceivers）本身的熱密度已高達必須額外加裝專屬水冷板的程度。這證實高密度 AI 算力在熱效能管理（Thermal Management）上已逼近現有材料科學的極限。
2. **半導體光刻極限與封裝複雜度（資料證實與推論）**：單一單體晶片（Monolithic Die）的物理尺寸受限於光刻機的光刻極限（Reticle Limit），過大會導致晶圓良率急遽下滑。 TPU 8 Max 雖然透過雙晶片單封裝解決了算力與記憶體擴充問題，但多晶片整合（Multi-Die Packaging）必然顯著提高半導體製造與測試的複雜度。
3. **長跨度 Agent 狀態保存的儲存負擔（合理推論）**：當 Agent 執行跨越數日（Multi-day）的任務，或因等待外部 API/人工輸入而頻繁進入休眠時，大量 MicroVM 的記憶體鏡像與磁碟快照，將對底層儲存階層（Storage Hierarchy）產生龐大的持久化 I/O 負擔與容量管理壓力。
4. **軟體生態系的遷移慣性（合理推論）**：儘管 Google 推出了原生支援 TPU 的 `torch TPU` 框架與開源推論引擎整合，但全球廣大 AI 開發者長期建立於 NVIDIA CUDA 與 GPU 生態系上的開發習慣與程式碼庫，完全消除轉移壁壘並落實零修改遷移仍需市場時間驗證。

---

## 7. 關鍵數字

* **7,800% 以上**：過去一年中，由 Agent 驅動的網路流量成長幅度。
* **50% 至 70%**：目前推論占全球所有 AI 算力消耗的比重（兩年前為 40%）。
* **24 倍**：預估至 2030 年全球 Token 需求的成長倍數（屆時每月超過 120 Quadrillion tokens）。
* **55 倍**：使現代 AI 在經濟上可行所需提升的算力強度倍數。
* **1.09**：Google 資料中心過去 12 個月平均的電力使用效率（PUE），營運能源負載比業界平均低 83%。
* **3 倍以上**：Google 資料中心目前每單位能量交付的算力效能較 5 年前的提升幅度。
* **30 倍**：2015 年第一代 TPU 較當時同級處理器提升的吞吐量倍數。
* **19.2 Tbps**：第八代 TPU 板卡上晶片間互連（Inter-chip Interconnect）的單晶片雙向頻寬。
* **9,600 顆**：第八代 TPU Superpod 包含的晶片數量（算力提升近 3 倍，訓練時間從數月縮至數週，成本降低 2.7 倍）。
* **16 hops 至 7 hops**：TPU 8i 採用 Boardfly 拓撲後，最差情況下的網路直徑縮減幅度（降低跨晶片通訊延遲達 50%）。
* **80%**：TPU 8i 為低延遲服務提供的每美元效能提升幅度。
* **288GB vs 384GB**：TPU 8i（288GB）與 TPU 8 Max（384GB）的 HBM 記憶體容量對比。
* **17.2 TB/s**：TPU 8 Max 的 HBM 記憶體頻寬（為 TPU 8i 8.6 TB/s 的 2 倍）。
* **768MB**：TPU 8 Max 每顆晶片整合的極速片上 SRAM 容量。
* **30%**：Google Axion ARM 架構處理器較下一代主要雲端業者提供的每美元效能優勢幅度（結合 RDMA 網路提升 40% 吞吐量）。

---

## 8. 什麼情況會改變這個局面

1. **Project Suncatcher 軌道雷射鏈路驗證**：若明年發射的雙衛星成功完成太空晶片間光學雷射鏈路測試，將驗證離地太陽能算力運作的可行性，進一步打破地面資料中心的電力與散熱限制。
2. **開源 Agent 執行環境（Agent Substrate）在 CNCF 的生態系擴散速度**：若 Kubernetes 社群廣泛採納 Agent Substrate 作為跨雲 Agent 運作標準，將破除單一雲端廠商的鎖定效應，加速 Agent 原生應用的跨雲普及。
3. **PyTorch 原生 TPU 後端（torch TPU）的零修改遷移落實度**：若開發團隊能真正實現「完全不修改程式碼」即在 TPU 上獲得媲美主流 GPU 的效能，將徹底改變 AI 加速晶片市場的雙雄競爭格局。
4. **晶圓代工極限與 Chiplet 封裝良率進展**：若多晶片封裝（如 TPU 8 Max 採用的雙晶片整合）的成本與良率無法持續優化，記憶體牆與算力密度的提升將面臨嚴峻的實體物理瓶頸。

如果您想深入閱讀更多關於 AI 基礎設施與硬體架構的開源研究，歡迎造訪 DeepValues Research 網站，或立即試用 DeepValues App。

---

## 9. 資料來源

* Google Cloud Tech - The Future of AI Infrastructure (講者: Amin Vahdat, Maria Biggs, Mark Lohmeyer)
