---
title: "解密 Discovery Loop：Jeff Dean 如何透過 AI 自動化實驗迴圈重塑科學與工程的未來"
date: "2026-11-09"
lang: "zh"
category: "ai"
tickers: []
notebook_id: "a5a4f080-0bc1-46d3-9c11-34b41a95f23d"
source_urls:
  - title: "Confronting Our AI Future: Closing Keynote \"Discovery Loop\" with Jeff Dean and Fei-Fei Li"
    url: "https://www.youtube.com/watch?v=ooGKNwJWdb8"
youtube:
  - title: "Jeff Dean Left Google to Make Science 20x Faster"
    url: "https://youtu.be/Cn0Cm4f0c1I"
    lang: "en"
  - title: "Google 27年老將Jeff Dean：物理法則否定AI無限進化"
    url: "https://youtu.be/_pzKloQ1SZ0"
    lang: "zh"
    publish_at: "2026-11-10T04:30:00Z"
podcast:
  - title: "Jeff Dean Left Google to Make Science 20x Faster | AI Explained"
    url: "https://open.spotify.com/episode/20wmMrZ09smH0QxvkCnVZk"
    lang: "en"
  - title: "Google 27年老將Jeff Dean：物理法則否定AI無限進化"
    url: "https://open.spotify.com/episode/7vEjxKEKYu0srCderqTMVn"
    lang: "zh"
generated_by: "NotebookLM + DeepValues editors"
disclosure: "AI-assisted"
---

# 解密 Discovery Loop：Jeff Dean 如何透過 AI 自動化實驗迴圈重塑科學與工程的未來

新創公司 Discovery Loop 由前 Google 首席科學家 Jeff Dean 攜手 Sanjay Ghemawat、Quoc Le 與 Oriol Vinyals 共同創辦，並採公共利益企業（Public Benefit Corporation, PBC）模式運作。該公司立足於人工智慧（AI）與科學工程的交會點，核心概念在於將傳統科學與工程研究中的「通用實驗迴圈」（Universal Loop of Science and Engineering）進行全自動化。透過結合前沿基底模型與自主 Agent（代理人）工具調用，系統能自動拆解子問題並執行數以萬計的平行實驗，利用強化學習（RL）與進化演算法從每次評估中持續自我學習。Discovery Loop 初期專注於機器學習研究、機器學習工程與硬體設計等數位領域，目標是將領域專家的生產力提升 20 倍至 50 倍。這項技術創新不僅將大幅縮減實驗迭代週期，更可望加速解決生醫保健、材料科學及美國國家工程院（NAE）所提出的 21 世紀重大工程挑戰，為全球科學研究與 AI 產業帶來深遠的範式轉移。

---

## 1. 核心問題與歷史瓶頸：為何傳統科學與工程實驗如此緩慢？

從第一性原理（First Principles）的角度審視，無論是開發下一代前沿大語言模型、設計先進的飛機，抑或是探索新型藥物分子，科學與工程研究本質上都遵循著一個共通的運作結構——「通用科學與工程實驗迴圈」（Universal Loop of Science and Engineering）。這個迴圈主要包含四個連續階段：

1. **提出實驗假設與方案（Propose Experiments）**：領域專家根據既有知識與經驗，構思可能改善系統效能或解決特定問題的假說。
2. **執行與實作實驗（Implement and Run Experiments）**：將假說轉化為程式碼、實體測試或計算流程，並投入資源進行運算與觀測。
3. **分析資料與測量結果（Examine Measurements and Results）**：收集實驗產生的各項指標與成果，進行量化評估與歸因。
4. **決定下一階段行動（Decide What to Do Next）**：依據分析結果，修訂原先的理論認知，並決定進行下一輪的實驗修正。

然而，在推動大型工程與前沿科學研究時，這套傳統迴圈正面臨嚴重的歷史瓶頸。首要問題在於**高度依賴人工手動操作**。在每一次迭代中，研究人員必須手動撰寫程式碼、設定參數、等待結果，並在凌晨或隔日回到辦公桌前分析資料，導致單次迴圈的等待時間過長。

更嚴重的瓶頸發生在**大型專案拆解（Decomposition）與協調成本**上。當研究問題過於龐大時，團隊必須將其拆解為數十個子問題，交由不同的跨部門小組平行處理。這不可避免地帶來了龐大的溝通協調成本（Coordination Overhead）、資源分配衝突以及複雜的大型系統效應。更棘手的是，一旦在專案初期確定了架構拆解方式，後續將極難靈活修正或重新審視早期決策。

根據 Jeff Dean 在 Stanford HAI 對談中的說明：「當你推動大型工程時，極難在專案啟動後有效重新審視那些早期的架構決策。」

Discovery Loop 旨在解決的核心難題，正是如何透過 AI 自動化這些實驗迴圈，大幅縮短單次實驗的迭代時間（Iteration Time）。透過讓系統自動進行問題拆解、平行執行數萬次實驗並從中學習，即使是少數的領域專家（Domain Experts），也能駕馭規模龐大且極具影響力的複雜科學問題。

---

## 2. 運作機制與技術解構：如何打造自動化的 AI 實驗迴圈？

### 自動化 AI 實驗迴圈的步驟解構

Discovery Loop 的系統架構設計，旨在建立一個能自主閉環、自適應學習的實驗平台。其運作機制可順序解構為以下四個階段：

* **第一階段：基底模型與 Agent 工具調用**
  系統以具備強大推理能力的前沿基底模型（Base Models）為核心，結合自主 Agent（代理人）系統，使其能夠靈活調用各種軟體與計算工具。
* **第二階段：自動拆解子問題**
  Agent 接收高階科學或工程目標後，自動將複雜大問題拆解為具體、可執行的子問題模組，減輕人類在專案規劃與架構拆解上的負擔。
* **第三階段：平行執行數萬次實驗**
  基於 Agent-First（Agent 優先）的基礎設施，系統能同時開啟數萬至數十萬個 Agent，平行執行大規模的實驗方案與運算任務。
* **第四階段：機器學習與自動化決策**
  系統利用強化學習（RL，Reinforcement Learning）與進化演算法（Evolutionary Algorithms），對每一次實驗結果與測量資料進行評估。系統會主動判斷「執行實驗 A 與實驗 B 的預期價值差異」，進而自動決定下一階段的最佳實驗方案，將經驗反饋至未來的提案機制中。

### 直覺比喻：廚師試做歐姆蛋 vs. 腦神經結構的學習

為了更直觀地理解這種自適應機制，可以運用人類學習的過程進行比喻：

假設一位廚師嘗試製作完美歐姆蛋。第一次下廚時，因為火候掌控不佳而把蛋煎焦；到了第十次，經過不斷調整時間與溫度，終於做出美味的歐姆蛋。這是一個典型的「從經驗中改善特定任務」的過程。

然而，更深層的進步發生在廚師的腦神經網絡中：在烹飪的過程中，大腦不只學會了煎蛋的步驟，更優化了「大腦如何吸收烹飪知識」的神經連接結構。這使得該廚師在未來學習做法式舒芙蕾或義式烘蛋時，能夠以快上數倍的速度掌握新技巧。Discovery Loop 的架構正是模仿這種機制，讓 AI 不僅能優化目前的實驗，還能從歷次解決問題的經驗中，優化「未來提出實驗提案」的能力。

### 核心概念釐清：自我改善（SI）與遞歸自我改善（RSI）的差異

在討論 AI 自動化實驗時，必須嚴格區分**自我改善（SI，Self-Improvement）**、**遞歸自我改善（RSI，Recursive Self-Improvement）**以及**機器學習（ML，Machine Learning）**等技術概念：

| 技術概念與縮寫 | 核心定義與運作機制 | 系統提案機制是否改變 | 具體應用範例 |
| :--- | :--- | :--- | :--- |
| **自我改善<br>(Self-Improvement, SI)** | 系統在固定目標下，針對特定模型或任務進行參數與架構優化。 | **保持固定**<br>提出新方案的基底系統本身並未改變。 | 針對 MRI（核磁共振造影）資料與診斷結果，自動優化影像分析模型的準確度。 |
| **遞歸自我改善<br>(Recursive Self-Improvement, RSI)** | 系統不僅優化特定任務的模型，更能進一步改善「負責提出改善方案」的基底系統本身。 | **動態進化**<br>系統具備「學習如何學習」（Learning to Learn）的能力。 | 系統在解決 5,000 個機器學習工程問題後，能汲取經驗優化自身的提案 Agent，使第 5,001 個問題的探索效率大幅提升。 |

---

## 3. 技術創新：從神經架構搜尋到 Agent 驅動的自適應系統

### 技術演進：從 Python 程式碼空間到自然語言驅動

探索自動化模型設計並非全新概念。約十年前，Discovery Loop 共同創辦人 Quoc Le 便曾推動**神經架構搜尋（NAS，Neural Architecture Search）**技術。然而，當時的技術條件存在重大限制：研究人員必須使用複雜、笨重的 Python 程式碼來手動定義搜尋空間（Search Space）。

現代的技術突破在於將前沿大語言模型（LLM，Large Language Model）與 Agent 系統深度整合。如今，研究人員不再需要寫死搜尋空間，而是能直接以**自然語言**向系統描述實驗目標與搜尋方向。例如，研究員只需指示：「請去探索有助於解析 MRI 影像的全新模型架構。」系統與 Agent 便能自動理解目標，展開高維度的架構探索。

根據 Jeff Dean 在 Stanford HAI 對談中的說法，這種從硬編碼搜尋空間轉變為自然語言驅動 Agent 的轉折，是電腦系統與 AI 系統能力上極為深遠（Profound）的範式轉移。

### Discovery Loop 的內部技術創新與營運實例

從 DeepValues Research 的 AI 基礎設施分析師視角來看，傳統軟體開發環境本質上是圍繞「數百名人類工程師」所建立的，其流程充滿了人工作業與非同步溝通的天花板。Discovery Loop 的創新作法在於徹底打破此架構限制：

* **自主 Agent Harness 系統**：開發了專屬的 Agent 協作 Harness 平台，支援人類與 AI 模型/Agent 之間的高度協作與設計審查（Design Review）。使用者不僅能與模型對話，還能邀請團隊成員共同進入介面，在提出新方案給 Agent 前進行即時討論、註解與設計修正。
* **「Agent 優先」（Agent-First）基礎設施**：Discovery Loop 從第一天起即打造能原生支援**十萬級別（Tens or Hundreds of Thousands）**自主 Agent 同時運轉的分散式基礎設施，使其能在幾小時內完成過去人類團隊需耗時數年的實驗規模。
* **實體營運與團隊建立**：在公司成立的前 3 週內，創始團隊於加州 Palo Alto 的 University Avenue 上的 Cafe Venetia 咖啡館連續進行了 **400 場**面試以篩選頂尖人才。目前公司總部租用了舊 Zibbo 餐廳空間（Funky Space），為團隊提供具備特色且極富創意的研發環境。
* **初步成果驗證**：在公司成立前數週內，團隊已在內部成功運行了約 **20 個自動化優化迴圈（Automated Improvement Loops）**，持續驗證實驗迭代速度與自適應學習效率。

---

## 4. 產業與實務影響：將領域專家生產力提升 20 至 50 倍

### 賦能領域專家與頂尖創始團隊遺產

Discovery Loop 的核心發展哲學，並非是用 AI 取代科學家或工程師，而是作為強大的生產力放大器。其確立的目標是將領域專家（Domain Experts）的生產力提升 **20 倍至 50 倍（20x to 50x）**。

這項企圖心建立在四位創辦人——Jeff Dean、Sanjay Ghemawat、Quoc Le 與 Oriol Vinyals——數十年來在 Google 所累積的深厚技術遺產之上：
* **分散式基礎設施與產品**：曾主導 MapReduce、BigTable、TensorFlow 的開發，並打造 Google Search、廣告系統（Ads）、Gmail、Google Translate 等關鍵服務。
* **AI 研究與前沿應用**：推動模型蒸餾（Model Distillation）、混合專家模型（MoE）、神經架構搜尋（NAS），以及應用於晶片設計的 AlphaChip（透過強化學習優化晶片布局）、蛋白質結構預測的 AlphaFold、AI 氣象預測（Neural Weather Forecasting）與 Gemini 大語言模型。
* **團隊頂尖人才陣容**：團隊成員包含 Go 語言專案領導者、Kimi K3 論文共同作者、Attention Residuals 論文作者；約 **10%** 的員工曾獲得 ACM 計算獎（ACM Prize in Computing），約 **10%** 曾獲國際資訊奧林匹亞（IOI）獎牌。此外，其團隊校友曾創辦 Anthropic、OpenAI 與 Physical Intelligence 等知名 AI 公司。

### 當前專注的三大數位領域與未來延伸

Discovery Loop 初期選擇將資源集中於三個全數位化（Digital Domains）領域：

1. **機器學習研究（ML Research）**
2. **機器學習工程（ML Engineering）**
3. **硬體設計（Hardware Design）**

**為何優先選擇數位領域？**
因為在數位領域中，整個實驗迴圈（程式碼撰寫、編譯、模擬、評估）可以做到 100% 軟體化與自動化，不會受到實體物理過程的等待限制，從而能將實驗迭代時間壓縮至極致。

當系統成功攻克 ML 工程與軟體自動化的瓶頸後，其技術能迅速延伸至更廣泛的實體科學與工程探索：
* **醫療保健（Healthcare）**：將自動化 ML 工具點對點應用於生醫影像與基因資料分析。
* **材料科學（Material Science）**：加速新型材料的電腦模擬與分子篩選。
* **解決 21 世紀重大工程挑戰**：完全符合 Discovery Loop 作為公共利益企業（PBC）的立案宗旨——利用前沿技術解決美國國家工程院（NAE）提出的 21 世紀重大工程挑戰（Grand Challenges），確保 AI 技術紅利能廣泛嘉惠大眾。

---

## 5. 物理極限與現實挑戰：迷思澄清與當前限制

### 澄清矽谷對 RSI 的過度炒作

當前矽谷與科技界對遞歸自我改善（RSI）存在諸多過度炒作，部分極端觀點認為 RSI 系統一旦啟動，將能以無窮快的速度自我迭代，在瞬間達到無限智力。

對此，Jeff Dean 給予了非常理性且基於物理事實的澄清。他強調，RSI 系統的運作依然嚴格受限於物理定律與算力硬體限制：

根據 Jeff Dean 在 Stanford HAI 對談中的說明：「你必須執行實際的計算與觀測，電腦需要時間運作並由模型分析資料，因此幻想實驗迴圈能無限快速運行是不切實際的。」

自動化系統確實能大幅提升研究進展的速率，但絕不可能脫離實體計算資源與時間的約束。

### 數學證明與理論科學中的 AI 局限

在近期的理論科學與數學領域（例如 AI 系統產出的 Lean 機器驗證證明），AI 展現了強大的硬解能力。然而，這也揭露了當前 AI 的技術限制：

* **缺乏優雅性與簡潔技術**：AI 產出的機器檢查證明往往長達 500 頁 Lean 程式碼。雖然成功驗證了命題是否成立，卻缺乏人類頂尖數學家（如 Terence Tao）所追求的簡潔與優雅（Elegant Techniques）。
* **理論提煉能力不足**：人類數學家在尋找優雅證明的過程中，往往會發明全新的數學工具與理論，進而啟發其他領域；而長達數百頁的機器證明目前難以直接轉化為具啟發性的新理論。

### 歷史預測偏差與拒稿故事的經驗啟示

回顧過去十幾年 AI 的發展歷程，Jeff Dean 分享了兩項重要的歷史預測偏差與一段傳奇經歷：

1. **神經網路架構並未走向極端有機化**：過去業界曾預測神經網路架構會發展出極其複雜、有機且具備不規則結構的柱狀形態。然而事實證明，主流的混合專家模型（MoE）依然維持高度規則化的結構（專家大小一致、定期匯聚），並未如預測般演化為野生的異構連結。
2. **程式編碼能力的關鍵解鎖作用**：在 Gemini 等大型模型的開發初期，團隊雖然重視 Coding 能力，但並未預料到「強大的程式編碼能力」會成為解鎖 AI 解決多元複雜問題、驅動 Agent 自動化的最關鍵解鎖因子（Key Unlocker）。
3. **2016 年 NeurIPS 拒稿事件**：2016 年，Jeff Dean 與 Geoff Hinton、Oriol Vinyals 合作撰寫的模型蒸餾（Model Distillation）論文投遞至 NeurIPS 頂會，當時審稿評語竟認為該論文「不太可能產生任何影響」而遭到拒稿。團隊隨後將論文發表於 arXiv 預印本平台，如今該論文已成為深度學習領域的基石之一，累積獲得約 **40,000 次**引用。

---

## 6. 關鍵數字

以下整理自 Sources 中提及的所有關鍵數據與指標：

* **團隊生產力目標**：將領域專家（Domain Experts）的生產力提升 **20 倍至 50 倍（20x - 50x）**。
* **早期團隊建置強度**：公司成立前 **3 週內**，團隊於 Palo Alto 的 University Avenue 上的 Cafe Venetia 進行了 **400 場**面試以招募頂尖人才。
* **團隊創始規模與轉變**：Jeff Dean 在 Google 曾管理高達 **4,400 人**的 Research 與 AI 團隊（以及 **600 人**的 Rating 評分團隊）；隨後透過單封 Email 轉變為僅 **4 名**直屬下屬（Geoff Hinton 退休後變為 **3 名**）。
* **團隊頂尖人才比例**：Discovery Loop 公司員工中約 **10%** 曾獲 ACM 計算獎（ACM Prize in Computing），約 **10%** 曾獲國際資訊奧林匹亞（IOI）獎牌。
* **內部運行規模**：早期已建立約 **20 個**自動化優化迴圈（Automated Improvement Loops），系統基礎設施設計可支援**數萬至數十萬個（Tens to Hundreds of Thousands）**自動化 Agent 同時運行。
* **歷史論文與引用資料**：
  * **2016 年**：模型蒸餾（Model Distillation）論文遭 NeurIPS 頂會拒稿，後發表於 arXiv，至今累積獲得約 **40,000 次**引用。
  * **2017 年 6 月 12 日**：Transformer 經典論文發表於 arXiv，正式開啟生成式 AI 時代。

---

## 7. 什麼情況會改變這個局面

對於關注 AI 產業與技術架構的專業人士與投資人，以下是未來 3 至 5 年值得持續追蹤的關鍵觀察指標：

1. **從數位領域跨足實體科學領域的進展**：
   觀察 Discovery Loop 的自動化實驗迴圈能否成功從純數位環境（ML 研究、硬體設計）擴展至需要結合實體化學、材料合成或生醫實驗的領域，以及其如何解決實體物理過程帶來的天花板限制。
2. **基底模型推理算力擴充與推理時間計算（Inference-time Compute Scaling）的成熟度**：
   觀察思維鏈（Chain of Thought）與推理階段算力擴充技術，能否顯著提升 Agent 在面對全新未解科學假說時的提案品質與創新度。
3. **機器生成證明的簡潔化與理論化工具的出現**：
   關注 AI 領域能否開發出新工具，將數百頁的機器驗證證明（Lean Proofs）自動提煉為人類可理解、具備高優雅性與啟發性的數學理論架構。
4. **公共利益企業（Public Benefit Corporation, PBC）商業模式的永續性驗證**：
   觀察 Discovery Loop 在秉持普及技術效益的公益使命下，如何平衡大規模算力基礎設施的巨大投入與長期商業化獲利能力。

---

深度理解 AI 技術架構的演進，是把握未來產業變革的關鍵。歡迎前往 DeepValues Research 官方網站閱讀更多深度開源研究報告，或使用 DeepValues App 獲取即時的產業分析與技術解構。

---

## 8. 資料來源

* *Confronting Our AI Future: Closing Keynote "Discovery Loop" with Jeff Dean and Fei-Fei Li*，發布單位：Stanford HAI（主講人：Jeff Dean，Discovery Loop 共同創辦人兼 CEO；對談人：Fei-Fei Li，Stanford HAI 創辦主任與 World Labs 共同創辦人兼 CEO）。
