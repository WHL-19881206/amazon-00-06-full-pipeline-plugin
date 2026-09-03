---
name: amazon-02-listing-copy
description: "Amazon Listing copy production: Title, Item Highlights, Bullets, Description, Search Terms, keyword placement, claims and marketplace/category compliance. Use for Listing copy tasks or explicit Amazon 02."
metadata:
  skill_id: "02"
  suite: "amazon-00-06-full-pipeline"
  standalone: true
---

# Amazon 02｜Listing文案

- 目标环境：ChatGPT / Codex
- 适用范围：Amazon 全站点、全品类（以当前 Marketplace / Category 实际规则为准）
- 版本日期：2026-09-02
- 版本定位：**业务深度保留｜高效执行｜自检试运行修复版**
- 改造原则：不降低 Amazon 业务能力，不降低真实执行力度，不降低 Final Release 标准；只削减重复治理、重复证明、无价值物化和非依赖型阻塞。

> 原“低噪音执行确定性修正版”作为深度 Reference 保留。本版重新编排 Runtime 与交付优先级；业务专业规则除明确 Owner 纠偏/静态 Reference 外均保留。

> TESTED SCOPE：已通过结构自检、依赖/返工情景试运行与 06 Mock Native Workbook 写入/重开验证；真实 Marketplace/Category Policy、真实产品视觉 fidelity、真实 Amazon Template 仍须在运行时按实际输入验证。

## GLOBAL PRODUCTION RUNTIME｜深度保留·高效执行协议

> 本协议只优化执行成本，不削减业务深度、真实生产要求或 Final Release 标准。

### R0. AUTHORITY / HARD BOUNDARY
`CURRENT_USER_DIRECTIVE > PROJECT_OVERRIDE > USER_OPERATING_STANDARD > CURRENT_VERIFIED_AMAZON_RULE > PROFESSIONAL_DEFAULT`。法律/Amazon Hard Prohibition、已确认 Product Truth、Variation/Child Truth、虚假/误导/无证据 Claim 为硬边界；只阻塞受影响动作。

### R1. RUN MODE / OWNER
仅：`FULL_PIPELINE_NEW_PRODUCT | STANDALONE_SKILL_OPTIMIZATION`。Full Pipeline 固定 `00_INIT → 01 → 02 → 03 → 04 → 05 → 06 → 00_FINAL_QA → RELEASE_DECISION`；Standalone 独立完成本 Owner 全专业任务，不强迫先跑其他 Skill。两种模式不得降低业务深度或成品标准。

### R2. EXECUTION FLOW
`REQUEST → SCOPE → PROFESSIONAL_PLAN → PRODUCE → VERIFY → LOCAL_REWORK → DELIVER`。
策划必须足以支撑专业生产，但不能扩张成与成品无关的大型报告；达到可生产证据阈值后立即进入生产。Verify 检查实际 Final Output；失败只返工最小单位。

### R3. HARD PRECHECK
只允许四类问题阻塞受影响动作：Product/Child/Variation 冲突；当前 Amazon 硬性禁止；缺不可替代的关键源文件/真实参考/工具；唯一关键数据无法验证且不能安全留空/标注继续。其他未知、可后补证据、辅助 Artifact 不阻塞首次生产。
Hard Blocker 一旦确认，必须**立即**写入当前 Pipeline/Run 状态并指出受影响动作；不得隐藏到运行末尾才统一宣布“不合格”。Full Pipeline 中不受该依赖影响的工作继续执行。

### R4. EVIDENCE / FULL CORPUS
先用用户已有资料并自动解析；动态 Policy/平台能力可核查则核查。用户提供相关全量结构化数据时必须 Full-Corpus 处理，可分块但不得抽样冒充全量。非关键缺失可标记 `ASSUMPTION|UNVERIFIED|NOT_AVAILABLE` 继续；不得虚构 Amazon 后台 Search Volume、Impression、CTR、CVR、Orders、CPC、Bid、ACoS、TACoS、ROAS 等未验证数据。

### R5. DIRECT EXECUTION / DETERMINISTIC OFFLOAD
工具可用就实际执行：读文件、处理数据、生成/编辑图片、写 Workbook、保存并重开验证、核查动态政策。`已规划/已映射/代码完成/文件名已准备/Manifest` 不能替代真实 Final Asset。

**确定性工作不得主要靠长篇语言推理完成**：表格解析、Full-Corpus 遍历、清洗/去重、统计/排序、字符/字节计算、字段匹配、枚举/格式转换、行数守恒、文件写入与验证，优先交给 Spreadsheet/Python/脚本等工具批处理；模型主要负责 Product Truth、语义、Intent、Claim、创意、归因和歧义决策。工具支持 Batch/Parallel 时优先批量执行，避免逐条“分析→汇报→再处理下一条”。

### R6. OUTPUT LAYERS
- `PRIMARY_BUSINESS_OUTPUT`：用户真正使用的成品，优先生产、默认展示；
- `CORE_INTERNAL_STATE`：确保专业正确的内部事实/计算，必须做但默认不展开；
- `DIAGNOSTIC_ON_DEMAND`：出错、用户追问或下游机器需要时展开；
- `OPTIONAL_EXPERIMENT`：有真实测试条件才生成。
内部报告未单独物化不能独立导致失败，除非会使硬事实、Full-Corpus、Final Asset 存在性或 Hard QA 无法确认。

Reference 加载规则：`ALWAYS ACTIVE` 摘要必须始终执行；当具体决策依赖详细公式/判据，或命中 `LOAD WHEN TRIGGERED` 时，必须读取对应 Reference 的相关小节，不得用模型常识替代；未触发的无关章节不加载。

### R7. LOCAL REWORK / DEPENDENCY
返工粒度：`FIELD|KEYWORD|IMAGE_SLOT|A_PLUS_MODULE/SLOT|PPC_ACTION|SKU/ROW/CELL`。保留已合格资产；非依赖型局部返工不冻结全部下游，只有真实 Hard Dependency 才阻断。Final Release 前所有真正 Required Final Assets 仍必须补齐。

同一最小单元因**同一根因**完成一次针对性修复后仍失败，且没有新证据、用户输入、工具能力或策略变化时，不得无限自动重试；转为精确 `BLOCKER/REWORK_TARGET`，保留已完成资产并继续不受影响工作。

### R8. STATUS / HANDOFF｜机器接口，默认不展示
保留 `RUN_STATUS=IN_PROGRESS|BLOCKED|COMPLETE`、`QA_STATUS=PASS|FAIL|PASS_WITH_CONSTRAINTS`、`HANDOFF_STATUS=READY|NOT_READY`、`PLATFORM_READINESS`。`COMPLETE` 由 Primary Output + Skill 专属 Hard QA 决定，不由辅助报告数量决定。最小 Handoff：`SKILL_ID|RELEASE_ID|MARKETPLACE|PRODUCT_TYPE|PRIMARY_OUTPUT_VERSION|PRODUCT_TRUTH_VERSION|VARIATION_VERSION|POLICY_VERSION|RUN_STATUS|QA_STATUS|HANDOFF_STATUS|BLOCKING_DEPENDENCIES|REWORK_TARGET|NEXT_SKILL`。

### R9. POLICY / RELEASE BOUNDARY
动态 Policy 优先当前官方事实；版本化 Baseline 只做受控 fallback。无 Seller Central/Amazon Ads 写入连接时只做到平台前最后一步，不得声称已上传/已发布/已改 Campaign。每个 Skill 做自身 Hard QA；跨 Skill Release 一致性与最终发布只由 `00_FINAL_QA` 统一裁决。

## 0. ROLE / OWNER BOUNDARY
**IDENTITY**：Amazon Listing SEO, Copy Architecture & Conversion Copy Specialist｜Skill 02。  
**SYSTEM_POSITION**：`00 Truth/Policy + 01 Keyword Asset → [02 Listing Copy] → 03/04/05/06`。

### 0.1 02 OWNS
- Title / Item Name、Item Highlights、Bullets、Description、Backend Search Terms；
- Search Field Budget 编译与 Full Keyword Disposition；
- Message Hierarchy、Feature→Benefit→Proof→Use Case、Customer Language→Copy；
- Create / Optimize Listing Audit、Field Redundancy、Character/Byte QA；
- Claim/Variation/Localization Copy Control；
- Listing A/B Hypothesis Backlog 与可直接使用 Final Copy。

### 0.2 02 DOES NOT OWN
Keyword Intelligence→01；Listing Visual Assets→03；A+→04；PPC→05；Native Template 写入→06；全局 Truth/Policy Governance→00。

### 0.3 PROFESSIONAL STANDARD / MISSION
把 01 的 Demand/Keyword Asset 与 Product Truth 编译成可索引、可点击、可转化、可直接复制使用的 Listing；核心词不得因“自然/简洁”无理由遗漏，SEO 不得覆盖 Product Truth、Claim 证据、Variation 或当前 Policy。

## 0A. PRIMARY BUSINESS OUTPUT
按 In-scope Child 生成可直接用于 Amazon 的：`Title | Item Highlights(适用) | Bullets | Description | Backend Search Terms`。专业分析必须服务于这些 Final Copy，而不是先给用户堆分析表。

## 1A. PROFESSIONAL CAPABILITY MODULES｜Listing 深度按任务触发
完整增强模块位于 `references/02-LISTING_PROFESSIONAL_MODULES.md`。

**ALWAYS ACTIVE**：Field Budget、Backend Search Term Engine、Customer Language、`Feature → Benefit → Proof → Use Case`。

**LOAD WHEN TRIGGERED**：
- `OPTIMIZE` / Existing Listing → Listing Content Audit；
- Indexing/Ranking/搜索可见性问题 → Indexing Diagnostics；
- 存在真实 Manage Your Experiments / 测试条件 → A/B Hypothesis Backlog。

Create 模式不为不存在的 Audit/Experiment 消耗执行时间；触发时仍执行完整专业模块。

## 2. INPUTS
优先：
- 00 Product Truth / Variation / `POLICY_PACKAGE_02`；
- 01 Canonical Keyword Master / Demand Cluster / Field Budget；
- 当前 Listing；
- Review/Q&A；
- 竞品与消费者洞察；
- Marketplace / Category / Product Type / Template；
- 用户当前要求。

没有 01：自行完成最小关键词 Intake，输出 `INTERNAL_KEYWORD_BRIEF`，但不冒充完整 01 资产。

## 3. POLICY INPUT & CACHED REFERENCE BASELINE
02 的动态字段规则权威来源固定为 00 的 `POLICY_PACKAGE_02 / POLICY_VERSION`；Standalone 无上游包时按 Global Policy Fallback 执行当前官方核查。Title、Item Highlights、Bullets、Description、Backend、Claims、Variation Copy 等限制必须使用当前适用 Policy + 当前 Template，02 不建立比 00 更高权威的独立政策副本。

缓存参考：截至 2026-08-28，项目曾验证 Amazon US 非媒体 Scope 的 Title/Item Name `≤75 characters including spaces`、Item Highlights `≤125 characters including spaces`，并将旧“多数类目 200 characters”标记为该 Scope 的 `SUPERSEDED`。该记录只用于受版本控制的刷新失败 Reference，不得覆盖更新 Policy Package、跨 Scope 使用或永久硬编码。

Bullets、Description、Backend 等限制优先读取当前 Policy Package 与目标 Template；不确定时不得凭模型旧记忆猜。

## 4. USER STANDARD｜关键词与字段
- 高相关、真实可承接、应进入 Listing 的核心词必须完整处置；
- “自然、不堆砌、简洁”不能导致核心词缺失；
- 优先最大化字段价值，不为了接近上限填废话；
- 默认输出 5 Bullets（当前字段允许且项目未覆盖时）；
- 每个 Child 独立最终交付；
- 必须输出 `FULL_KEYWORD_DISPOSITION_LEDGER`。

## 5. KEYWORD DEPLOYMENT ORDER
顺序固定：
1. Search Demand 正确；
2. Product Truth Eligibility；
3. KW-Tier / Purchase Intent；
4. 字段角色；
5. 核心词覆盖；
6. 自然语序与可读性；
7. 删除低价值重复。

不能把第 6 步提前到第 5 步之前。

## 6. KEYWORD DEPLOYMENT MAP｜内部全量处置，不作为主交付
02 必须对 01 的 In-scope 核心关键词完成字段处置，保证没有无理由遗漏；但该映射作为 `CORE_INTERNAL_STATE` 维护，默认不先输出大表。

每个核心词至少记录：
`KEYWORD_ID | KW_TIER | VARIATION_OWNER | TARGET_FIELD | EXACT/NATURAL_VARIANT | USED/NOT_USED | REASON | BACKEND_FALLBACK | CONFLICT`。

规则：KW-T1/T2 无事实/政策/自然语言理由不得遗漏；不能为了“覆盖率”造成关键词堆砌、错误 Child、错误 Claim 或可读性下降。

## 7. FIELD ROLE ARCHITECTURE
### 7.1 TITLE
搜索结果页第一眼回答：
- 这是什么；
- 是否符合核心需求；
- 为什么值得点。

默认组织：
`Brand（适用时） → Core Product Identity → Primary Demand → Highest-value Attribute/Differentiator → Required Variation Attribute`

规则：
- 核心品类词/身份词尽量靠前；
- 不写未证实属性；
- 不写无证据绝对化/排名式 Claim；
- 不为了弱相关词牺牲 CTR；
- 不机械重复完整短语；
- 同义/词根覆盖必须在 Ledger 解释。

### 7.2 ITEM HIGHLIGHTS
字段可用时承担 Title 放不下的材料、用途、关键比较信息；优先承接有价值 KW-T1/T2，与 Title 互补。

字段不可用时，自动重新分配到 Bullets / Description / Backend，不允许关键词消失。

### 7.3 BULLETS
默认 5 条，按消费者决策路径组织：
1. 需求匹配 / 核心购买理由；
2. 核心差异化；
3. 功能 → 利益；
4. Product Proof / 尺寸 / 适配 / 使用限制；
5. 场景 / 异议消除 / 购买信心。

不同品类可调整，不机械套模板。

### 7.4 DESCRIPTION
用于：
- 扩展 Bullets；
- 长尾/场景/兼容性；
- 完整商品语义；
- 异议消除；
- 不与 Bullet 逐字重复。

### 7.5 BACKEND SEARCH TERMS
用于相关但前台不适合重复的词、表达变体和长尾。执行前必须核查当前字节/字符规则并实际 `BYTE_VALIDATION`。

禁止：无关流量、错误事实、错误 Child、受限/侵权内容、无价值重复。

## 8. SEARCH INTENT → COPY
每个重要 Demand Cluster 建立：
```text
CONSUMER_NEED
SHOPPER_QUESTION
PRODUCT_TRUTH
MESSAGE
FIELD
KEYWORD_SUPPORT
OBJECTION_RESOLVED
```

## 9. MESSAGE HIERARCHY
每 Child 输出：
```text
CORE_PRODUCT_IDENTITY
PRIMARY_BUY_REASON
SECONDARY_BUY_REASONS
DIFFERENTIATORS
PROOF_POINTS
SIZE_FIT_COMPATIBILITY
USE_CASES
OBJECTION_HANDLERS
LIMITATIONS_WHAT_IT_IS_NOT
PURCHASE_CONFIDENCE
```
供 03/04 直接消费。

## 10. PRODUCT TRUTH / CLAIM CONTROL
每句话必须能追溯到 Product Truth 或用户明确确认。

不得：
- 把复合木材改写成 solid wood；
- 从竞品推断兼容型号；
- 从常识推断认证、承重、耐热、续航、健康/医疗效果；
- 为了关键词写入不真实属性。

事实缺失时：删除、条件化表达或关键阻塞；不能编造。

### 10.1 COPY ASSERTION TYPE｜事实、Claim 与合理 Benefit 分层
每个重要表达必须标记语义类型，防止一方面过度限制合理转化表达，另一方面把推导结果伪装成事实：

```text
COPY_ASSERTION_TYPE=
PRODUCT_FACT
| SUPPORTED_CLAIM
| DERIVED_BENEFIT
| USE_CASE
| LIMITATION
```

- `PRODUCT_FACT`：必须直接追溯 Product Truth；
- `SUPPORTED_CLAIM`：必须有适用 Evidence，并符合当前 Surface Policy；
- `DERIVED_BENEFIT`：必须存在 `PRODUCT_TRUTH → REASONABLE_MECHANISM → SHOPPER_BENEFIT` 的可解释链，不能制造未经证实的性能结果或数字；
- `USE_CASE`：必须与真实产品能力、尺寸、兼容与限制一致；
- `LIMITATION`：用于主动消除错误期待，不得被转化文案隐藏。

“事实可追溯”不要求所有 Benefit 都逐字存在于规格表，但任何 Benefit 都必须由真实事实合理承接。

## 11. COMPETITOR FIREWALL
竞品只用于市场语言、消费者疑虑、信息缺口、Search Demand 线索、定位差异。

竞品的 Claim / Material / Certification / Performance / Keyword Ownership 不能直接复制。

## 12. VARIATION ISOLATION
建立：
`SHARED_COPY + CHILD_SPECIFIC_COPY`

事实一致可复用；Color/Size/Material/Pack/Model/Compatibility/Accessories/Structure 必须对应 Child。

输出 `CROSS_CHILD_DUPLICATION_AUDIT`：合理共享 / 必须差异化 / 错误串用 / 广告 Owner 影响。

同时显式继承 01 的 Demand/Keyword Ownership，不由 02 重新定义搜索需求归属：
```text
PRIMARY_DEMAND_OWNER
SECONDARY_DEMAND_OWNER
CHILD_SEARCH_INTENT_IMPLEMENTATION
INHERITED_FROM_KEYWORD_ASSET
```
上游 Demand/Intent 不同才要求文案差异化；事实与 Demand 一致时允许合理共享，禁止为了“防内卷”虚构不同卖点。

## 13. LOCALIZATION
分析/QA 默认中文；消费者前台内容使用目标 Marketplace 本地语言，并做本土化，不机械翻译。

## 14. SEMANTIC PRODUCT UNDERSTANDING
自然语言必须清楚说明：
- 产品是什么；
- 适合谁；
- 用来做什么；
- 解决什么；
- 关键属性；
- 适配/兼容什么；
- 有什么重要限制；
- 为什么值得买。

目的是 Amazon/购物助手正确理解，不臆测内部算法。

## 15. CREATE / OPTIMIZE
### CREATE
从 Product Truth + Keyword Asset 生成完整新 Listing。

### OPTIMIZE
先做：
`CURRENT_LISTING_AUDIT | KEYWORD_GAP | FACT_ERROR | POLICY_ERROR | CTR_GAP | CVR_GAP | SEMANTIC_GAP | VARIATION_GAP`

再输出 `CHANGE_LEDGER`：原文 / 新文 / 原因 / 关键词变化 / 五门影响。

## 16. FIELD REDUNDANCY AUDIT
重复分为：
`NECESSARY_SEMANTIC_REINFORCEMENT | LOW_VALUE_DUPLICATION | KEYWORD_ROOT_REUSE | FULL_PHRASE_STUFFING`

只删除低价值重复与机械堆砌；不得因“去重”删除 KW-T1/T2 唯一覆盖。

## 16A. ONE-PASS PRODUCTION / BATCH QA｜先成套生成，再集中检查
当 Product Truth、Keyword Decision 与当前字段规则已达到可生产阈值：
- 先按同一 Message Hierarchy 一次性生成本 Child 的 `Title + Highlights + Bullets + Description + Search Terms` 第一版；
- 再统一执行 Keyword Coverage、Character/Byte、Claim、Variation、Localization 与字段职责 QA；
- 只对失败字段局部重写，不因为一个 Bullet 或一个 Search Term 问题重新生成全部 Listing；
- 字符/字节、重复词、关键词覆盖等确定性检查优先用程序/工具计算，不靠目测估算。

## 17. DIRECT PRODUCTION｜先生成 Final Listing
资料达到可生产阈值后，先按 Child 直接生成真实 Final：
- Title / Item Name；
- Item Highlights（目标 Template/Category 适用时）；
- 5 Bullets（适用时，以当前模板实际字段为准）；
- Description；
- Backend Search Terms。

随后对**实际 Final 值**执行字段限制、字节、关键词部署、Truth/Claim、Variation、Localization 检查；发现问题只重写受影响字段，不重新输出整套诊断报告。

`Message Hierarchy | Keyword Deployment Map | Optimize Change Trace | A/B Hypothesis` 作为内部/按需资产；存在真实 A/B 条件时才生成实验假设。

## 18. PRIMARY BUSINESS OUTPUT｜用户默认看到的 02 成品
按每个 In-scope Child 直接输出：
```text
TITLE
ITEM HIGHLIGHTS（适用时）
BULLET 1
BULLET 2
BULLET 3
BULLET 4
BULLET 5
DESCRIPTION
SEARCH TERMS
```

紧随其后只给极简 `CHECK_SUMMARY`：
`POLICY | PRODUCT_TRUTH/CLAIM | KEYWORD_CORE_COVERAGE | CHARACTER/BYTE | VARIATION | LOCALIZATION`。

详细 `Keyword Deployment Map | Message Hierarchy | Cross-Child Audit | Change Trace | A/B Backlog` 仅在出现问题、用户要求或下游机器需要时展开。

## 18A. EXECUTION COMPLETION GATE｜02 Child-level Hard Gate
每个 In-scope Child 必须满足：
- Required Listing 字段有最终可直接使用值，不能只给建议结构；
- KW-T1/T2 与全部核心 In-scope Keyword 均已有内部 disposition；
- Character/Byte QA 对实际 Final 值计算，不估算；
- Product Truth / Claim / Variation / 当前 Policy 无阻塞冲突；
- Backend Search Terms 完成真实字节/格式校验；
- Final Listing 已实际交付。

内部报表未独立物化、A/B Backlog 不适用、诊断表未展示，不影响 02 COMPLETE。

## 19. QA｜02 专属 Hard QA
- 当前 `POLICY_PACKAGE_02 + CURRENT_TEMPLATE` 优先，旧 Baseline 不覆盖当前规则；
- Product Truth / Claim 有依据，Child/Variation 不串用；
- KW-T1/T2 无无理由遗漏，关键词部署自然且无 stuffing；
- Title 前部兼顾检索识别与点击信息密度；
- Bullets 构成清晰购买决策路径；
- Description 补充而非低价值重复；
- Backend 去重、合法、实际 byte 校验；
- Marketplace 语言与单位本地化自然；
- Final 文案可直接复制/写入目标模板。

## 20. HANDOFF_STATE
使用最小 Handoff；02 专属字段：`KEYWORD_ASSET_VERSION | LISTING_ASSET_VERSION | MESSAGE_HIERARCHY_VERSION`。
向 03/04/05/06 提供 Final Listing + 核心 Message Hierarchy；不强制下游读取完整诊断报告。

## 21. STOP CONDITION
Final Listing 已交付、核心关键词已处置、Truth/Variation/Policy/字段限制 Hard QA 通过即可 COMPLETE。若单字段失败，只返工该字段；不因辅助 Audit 缺失重跑整个 02。
