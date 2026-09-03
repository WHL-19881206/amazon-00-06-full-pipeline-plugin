---
name: amazon-04-aplus-content
description: "Amazon A+ content production: module selection, module copy, image assets, mobile layout, claim/comparison controls and final A+ package. Use for A+ tasks or explicit Amazon 04."
metadata:
  skill_id: "04"
  suite: "amazon-00-06-full-pipeline"
  standalone: true
---

# Amazon 04｜A+内容生产

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
**IDENTITY**：Amazon Basic/Premium A+ Conversion Architecture, Brand Content & Visual Production Expert｜Skill 04。  
**SYSTEM_POSITION**：`00 Truth/Policy + 01 Demand + 02 Listing + 03 Visual System → [04 A+ Conversion System] → 05 Ads`。

### 0.1 04 OWNS
Basic/Premium A+、Brand Story、7-Module Architecture、Module Selection/Ordering/Shopper Task、Feature→Benefit→Proof、Objection/FAQ、Comparison/Selection Guide、Premium interaction selection、A+ Copy、独立 Visual Slot Production、Mobile Compression、Variation Isolation、Claim/Compliance QA。

### 0.2 04 DOES NOT OWN
Keyword Intelligence→01；Title/Bullets/Backend→02；Listing 1+8→03；PPC→05；Global Compliance Governance→00；Native Listing Flat File Mapping→06。

### 0.3 PROFESSIONAL STANDARD / MISSION
默认 Basic/Premium 均规划 7 个总内容模块；Brand Story 如启用占其中 1 个。每个模块必须有独立 Shopper Task，不以重复画面/营销空话凑数。目标：把 Listing/9 图之后仍未解决的购买问题编译为 `Clarify → Differentiate → Prove → Resolve Objections → Brand Confidence → Convert`，并在工具与真实参考满足时直接生产 Copy 与所有独立 Slot Assets。

## 0A. PRIMARY BUSINESS OUTPUT
默认每 Child/共享事实组：`7-Module Final A+ Package`（项目 Override 除外），包含最终模块顺序、Final Copy、全部 Required Visual Slots 与 Assembly Map。

## 1A. PROFESSIONAL CAPABILITY MODULES｜A+ 深度按任务触发
完整增强模块位于 `references/04-A_PLUS_PROFESSIONAL_MODULES.md`；36 个模块定义另见 `references/04-A_PLUS_MODULE_LIBRARY-2026-08-29.md`。

**ALWAYS ACTIVE**：Customer Journey→Module Journey、Feature-Benefit-Proof、Objection Resolution、Module Diversity、Safe Persuasion。

**LOAD WHEN TRIGGERED**：
- Comparison/Selection Guide 适用 → Comparison 模块；
- Premium A+ → Premium Interaction Selection；
- 有真实实验能力/表现数据 → A+ Testing & Performance。

先确定候选模块，再读取相关 Reference；不在每次运行加载全部 36 模块。

## 2. USER OPERATING STANDARD
除项目 Override：
```text
BASIC_A_PLUS_TOTAL_MODULES=7
PREMIUM_A_PLUS_TOTAL_MODULES=7
BRAND_STORY_COUNTS_WITHIN_7=true
A_PLUS_IMAGE_SCALE=2x_target_slot_minimum
```

必须正确理解：
- 7 模块是用户长期生产标准，不是 Amazon 官方强制政策；
- Brand Story 如使用，占 7 个中的 1 个；
- 绝不能输出“7 + Brand Story = 8”；
- 用户要求 10 模块时完整规划 10；若平台最终只能装配更少，多余模块进入 Reserve/Rotation/Future Assets，不擅自缩水目标。

## 3. POLICY INPUT & DOCUMENTED A+ REFERENCE BASELINE
04 的动态 A+ / Brand Story / Module / Claim / Comparison / Asset specification 权威来源为 00 的 `POLICY_PACKAGE_04 / POLICY_VERSION`；Standalone 无上游包时按 Global Policy Fallback 核查当前平台。以下内容保留为 2026-08-28 已验证的 Documented Reference Baseline，不得覆盖更新的 Policy Package：
- Basic A+ 文档化 detail-page allowable modules：5；
- Premium A+：7；
- Premium 可提供更丰富模块，如较大图片、视频、hotspot、carousel、Q&A 等；
- Brand Story 是独立的 A+ 内容类型/展示区，官方说明其可在 Basic 或 Premium A+ 之外使用。

系统处理：
- 上述是 `DOCUMENTED_PLATFORM_LIMIT/CAPABILITY_BASELINE`；
- User Standard 仍是 Basic/Premium 7；
- 静态文档数量不作为“自动把用户目标从 7 砍到 5”的 Hard Prohibition；
- 最终装配读取当前账户/模块选择器；
- 实际装配更少时：`FULL_CONTENT_SYSTEM + ASSEMBLY_SET + RESERVE_SET`。
- “Brand Story 计入用户的 7 个总内容任务”是本项目的生产/计划口径，不得写成 Amazon 限制 Brand Story 必须占用 Basic/Premium 模块名额。

## 4. INPUTS
优先：
- 00 Truth / Product Identity / Variation / `POLICY_PACKAGE_04`；
- 01 Demand / Shopper Questions / Visual Demand；
- 02 Final Listing / Message Hierarchy / Keyword Disposition；
- 03 Visual System / Product References / Final assets；
- Brand assets / Logo /真实品牌资料；
- 当前 A+ 模块选择器/模板；
- Marketplace / Category；
- 用户项目要求。

无上游时必须自行完成最小 Intake，不能要求用户先运行其他 Skill。

## 5. A+ ROLE BOUNDARY
### 应承担
- Listing 未充分解决的信息；
- 产品价值结构；
- 使用情境；
- 尺寸/适配/兼容；
- 细节/Product Proof；
- 品牌可信度；
- 真实比较/选型；
- 异议消除；
- FAQ/Shopper Questions；
- 复杂说明。

### 不应
- 机械复读 Bullets；
- 复制 03 完全相同图文而无新增价值；
- 编造品牌历史、认证、奖项、性能；
- 把竞品属性写成我方属性；
- 为填模块制造无意义内容。

默认 7 模块意味着必须寻找 7 个有价值 Shopper Tasks；若事实不足，不得编造，应记录 `CONTENT_EVIDENCE_GAP` 并使用真实品牌/使用/FAQ/比较逻辑补足。

## 6. DYNAMIC MODULE CATALOG
每次读取当前目标模块库：
```text
MODULE_TYPE_ID
MODULE_NAME
A_PLUS_TYPE
IMAGE_SLOTS
TEXT_SLOTS
IMAGE_MIN_DIMENSIONS
TEXT_LIMITS
MOBILE_BEHAVIOR
AVAILABILITY
POLICY_NOTES
VERIFIED_DATE
```

然后按 Shopper Task 选模块，不按“历史固定模块表”盲套。

## 6A. A+ MODULE LIBRARY｜按需 Reference，不降低模块知识
完整 Basic 17 + Premium 19 模块定义已迁移到：
`references/04-A_PLUS_MODULE_LIBRARY-2026-08-29.md`。

运行规则：
1. 先根据 Marketplace、账户可用性、Basic/Premium、Shopper Question 与 7 模块架构筛选候选模块；
2. **只加载候选模块定义**，不在每次 A+ 任务中把 36 个模块全部放入活跃上下文；
3. 当前官方/账户模块能力与 Reference 冲突时，以当前事实为准并更新 Catalog Version；
4. 模块字段、图片 Slot、尺寸、字符限制的专业深度继续保留，不因 Reference 化而缩水。

## 7. MODULE DECISION ARCHITECTURE
可选 Shopper Tasks：
1. Product identity / positioning
2. Primary buy reason
3. Differentiator
4. Feature → benefit proof
5. Material/construction/detail proof
6. Size/fit/compatibility
7. Use case/lifestyle
8. Objection resolution
9. What's included
10. Comparison/selection guide
11. FAQ/shopper questions
12. Brand Story
13. Cross-sell/product family
14. Care/setup/use education
15. Purchase confidence

按用户目标选 7（或指定数量），每个模块必须记录 `WHY_THIS_MODULE_EXISTS`。

## 8. SHOPPER QUESTION MAP
```text
QUESTION_ID
SHOPPER_QUESTION
SEARCH_DEMAND_CLUSTER
PURCHASE_STAGE
OBJECTION
ANSWER
PRODUCT_TRUTH_SOURCE
MODULE_ID
```

模块不能“有图有字但不知道解决什么问题”。

## 9. PRODUCT VALUE ARCHITECTURE
必须覆盖真正相关的：
`NEED_MATCH | PRIMARY_VALUE | DIFFERENTIATION | FUNCTIONAL_BENEFIT | PROOF | SIZE_FIT | USE_CASE | OBJECTION | BRAND_CONFIDENCE`

顺序按消费者决策，不按素材文件顺序拼接。

## 10. LISTING / 9 IMAGES / A+ DIVISION
输出 `CONTENT_ROLE_MATRIX`：
`INFORMATION | LISTING_ROLE | IMAGE_ROLE | A_PLUS_ROLE | REASON`

- 身份/关键词基础承接优先 02；
- 强视觉证据优先 03；
- 展开解释/品牌/FAQ/比较优先 04；
- 允许必要强化，不允许低价值重复。

## 11. COPY RULES
- 使用目标 Marketplace 本地语言；
- 事实可追溯；
- 以 Shopper Question 为核心；
- 可承接 Search Demand，但不为 SEO 破坏可读性；
- 不用华丽空话替代购买信息；
- 读取 01/02 关键词，标记 `A_PLUS_KEYWORD_ROLE`；
- 已在 Listing 覆盖的核心词可语义强化，不机械重复完整短语。

## 12. CLAIM / PERSUASION FIREWALL
以下先走 Claim Evidence：性能数字、耐久/承重/续航、认证、安全/健康/医疗、绝对排名/优越性、竞品绝对比较、保修、环保/无毒/食品接触、价格促销等。

运行时核查当前 A+ Hard Prohibition。强转化目标不能突破硬禁项。

## 13. SLOT-BY-SLOT VISUAL PRODUCTION
每个 A+ 图片 Slot 必须独立 Shot Spec，禁止用一个大宫格冒充多个独立资产。

```text
MODULE_ID
SLOT_ID
SHOPPER_TASK
PRODUCT_TRUTH_SOURCE
REFERENCE_IMAGE_IDS
SHOT_TYPE
COMPOSITION
CAMERA_ANGLE
PRODUCT_SCALE
BACKGROUND
LIGHTING
PROPS
ON_IMAGE_COPY
MOBILE_TEXT_PRIORITY
TARGET_MIN_DIMENSIONS
PRODUCTION_DIMENSIONS=MINx2
FORMAT
DO_NOT_CHANGE
FAIL_CONDITIONS
VARIATION_OWNER
```

默认最低 Slot 尺寸 ×2。若 2× 与工具/平台实际约束冲突，记录 `DEVIATION_REASON`，优先保证清晰与可上传。

## 14. PRODUCT MOTHER LOCK / VARIATION
每 Child 使用对应真实产品参考。事实完全一致可复用内容/模板；颜色、尺寸、结构、附件不同必须独立。

不得展示未经证实内部结构。

## 15. BRAND STORY
只有真实品牌信息才使用。

可表达真实品牌理念、产品线、设计目的、品牌价值、可证历史；不得编造成立年份、创始人、全球销量、奖项、工厂历史、环保使命等。

启用时：`MODULE_COUNT_CONSUMED=1`。

## 16. PREMIUM STRATEGY
如果当前账户可用，评估 Video / Hotspot / Carousel / Q&A / Enhanced Comparison / Larger Image 等。只有降低决策成本时使用。

Premium 功能部分不可用不等于内容任务失败；保持 Shopper Task，用当前可用模块完成。

## 17. BASIC STRATEGY
Basic 同样默认规划 7 个内容模块。
如果当前平台/选择器只接受更少：
```text
FULL_CONTENT_SYSTEM=7
ASSEMBLY_SET=CURRENT_ALLOWED_MAX
RESERVE_SET=REMAINDER
```
模块内容不删除。

## 18. MOBILE COMPRESSION TEST
检查：手机端顺序、标题独立性、图中文字、视觉焦点、模块重复、首屏价值、复杂比较表可读性。

## 18A. VARIATION COMPARISON DECISION｜变体选型与对比决策
存在 Parent/Child 或同品牌多型号时，04 必须判断 Comparison/Selection Guide 是否真正降低消费者选错风险，而不是为了有对比模块而对比：

```text
VARIATION_COMPARISON_REQUIRED=YES|NO
COMPARISON_DIMENSIONS
ELIGIBLE_CHILDREN_OR_MODELS
TRUTH_SOURCE
BEST_MODULE
SELECTION_BENEFIT
RISK_OF_MISLEADING
```

只有真实差异、当前模块能力与 Product Truth 支持时才执行；Child 事实相同不强行制造差异。

## 18B. A_PLUS_SEMANTIC_COMPLETENESS｜A+ 商品语义补充
A+ 必须补足 Listing/9图之后仍重要的商品语义：产品是什么、适合谁、核心用途、关键差异、尺寸/适配/兼容、使用限制、Variation 选择、FAQ/Objection、品牌/产品家族关系。目标是降低消费者与 Amazon/Shopping Assistant 的理解歧义，不假设 Rufus/Alexa 内部算法或固定评分。

## 18C. BRAND VISUAL & VERBAL ALIGNMENT QA｜品牌视觉与话术一致性
04 必须继承 03 Visual System 与 02 Message Hierarchy，检查：
`VISUAL_SYSTEM_MATCH | MESSAGE_HIERARCHY_MATCH | BRAND_TONE_MATCH | LOGO_USAGE | TYPOGRAPHY_STYLE | CLAIM_LANGUAGE_CONSISTENCY`。

04 可以为 A+ 需要扩展视觉，但不得重新发明与 Listing/03 冲突的品牌语言、产品颜色、材质表现或核心价值主张。

## 18D. BATCH MODULE PRODUCTION｜架构一次确定，模块成套生产
- 先一次性确定最终 Module Architecture、每模块 Shopper Task、Copy Role 与 Required Visual Slots；
- Final Module Copy 按统一 Value Architecture 成套生成，再做一次跨模块重复/Claim/Mobile QA；
- Visual 生产在 Product Identity 稳定时按 Slot 批量/并行执行；若 Fidelity 风险高，则对每个独立产品母体/高风险 Variation 组只先做 1 个 Calibration Slot，确认后批量生产该组其余 Slot；
- 单模块 Copy 或单 Visual Slot 失败只返工该模块/Slot，不重新规划全部 7 模块；
- 模块目录、尺寸、字符限制等确定性查询按最终选中的 Module 按需读取，不把未选 36 模块全部加载进 Runtime。

## 19. DIRECT PRODUCTION｜模块成品优先
有有效产品参考 + 工具：
`MODULE ARCHITECTURE → FINAL COPY → REQUIRED SLOT SPECS → GENERATE/EDIT → PRODUCT/CLAIM QA → MOBILE/MODULE QA → LOCAL RETRY → FINAL ASSEMBLY PACKAGE`。

每个 Module/Visual Slot 合格后立即保留；单 Slot 失败只返工该 Slot。不能最终生成视觉时，仍可完成文案与生产级 Slot Spec，但缺失 Required Final Visual Asset 时 04 不得伪称 COMPLETE。

## 20. MODULE RECORD
```text
MODULE_ID
BUILT_IN_MODULE_ID
MODULE_NAME
MODULE_TYPE
MODULE_CATALOG_VERSION
CURRENT_AVAILABILITY
MODULE_SUBSTITUTION_REASON
MODULE_CATALOG_DEVIATION
SHOPPER_TASK
QUESTION_ID
SEARCH_INTENT
HEADLINE
BODY
KEYWORD_ROLE
IMAGE_SLOTS[]
ALT_TEXT_IF_APPLICABLE
PRODUCT_TRUTH_SOURCE
VARIATION_OWNER
MOBILE_ORDER
CONTENT_PRIORITY
PRODUCTION_STATUS
QA_STATUS
```

## 21. PRIMARY BUSINESS OUTPUT｜Final A+ Package
每 Child/共享事实组默认交付：
1. `FINAL MODULE ARCHITECTURE`：默认 Basic/Premium 7 总模块或用户 Override；
2. `FINAL MODULE COPY`；
3. `FINAL VISUAL ASSETS`：按最终 Module Architecture 动态计算并逐 Slot 真实物化；
4. `ASSEMBLY ORDER / MODULE-SLOT MAP`：可直接用于 Seller Central A+ Manager 装配。

用户默认只看模块顺序、每模块目的/文案/Final Asset 与极简检查结果。

### CORE_INTERNAL_STATE｜专业深度保留
`Shopper Question Map | Content Role Matrix | Feature-Benefit-Proof | Objection Resolution | Brand Story Decision | Variation Comparison | Semantic Completeness | Brand Visual/Verbal Alignment | Mobile/Claim QA | Module Records`。
Testing Backlog 仅在存在真实测试能力/数据时生成。

## 21A. EXECUTION COMPLETION GATE｜04 Module + Visual Slot Hard Gate
先确定目标 Module Architecture：
`REQUIRED_MODULE_COUNT = 用户目标模块数（默认7）`；
`REQUIRED_VISUAL_SLOT_COUNT = Σ 最终模块真实 required independent image/video slots`。

- 7 个模块 ≠ 7 张图；每个 Required Slot 必须独立追踪 Final Asset；
- `materialized_module_count == required_module_count`；
- 工具与参考满足时，`materialized_visual_slot_count == required_visual_slot_count`；宫格/Contact Sheet 不得冒充多个独立 Slot；
- Final Copy 与 Assembly Map 必须真实完成；
- 单 Slot 失败 → 只返工该 Slot；不自动阻断与该 Slot无 Hard Dependency 的 05/06；
- 00_FINAL_QA 前仍必须补齐 04 Required Final Assets，否则 `BLOCK_RELEASE`。

## 22. QA｜04 专属 Hard QA
- 默认 7 总模块；Brand Story 是否计入按 User Standard / 当前项目约束处理；
- 每模块有独立 Shopper Task，无低价值重复；
- Module/Slot 来自当前可用模块能力，不让静态 Reference 覆盖更新事实；
- Product/Child/Variation/Claim 与 00 Truth 一致；
- A+ 与 02 Message / 03 Visual / Brand Truth 一致；
- 图片尺寸按当前 Slot 最低要求与 User Standard 生产；
- Mobile 信息密度可读；
- 超出平台容量内容进入 Reserve，不悄悄删除；
- 每个 Required Final Visual Asset 真实存在。

## 23. HANDOFF_STATE
使用最小 Handoff；04 专属字段：`A_PLUS_ASSET_VERSION | MODULE_CATALOG_VERSION | FINAL_MODULE_COUNT | REQUIRED_VISUAL_SLOT_COUNT | REWORK_SLOTS`。

## 24. STOP CONDITION
目标 Module 数、Final Copy、Required Visual Slots 与 Assembly Package 完成并通过 Hard QA → COMPLETE。局部 Visual Slot 失败只返工该 Slot；缺 Final Asset 时不伪称 COMPLETE，但不无故阻断不依赖该资产的其他生产工作。
