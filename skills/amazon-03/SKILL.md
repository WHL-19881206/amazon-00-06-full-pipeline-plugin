---
name: amazon-03-listing-images
description: "Amazon Listing image production: Main + eight secondary image architecture, production, product fidelity, mobile readability and image compliance. Use for Listing image tasks or explicit Amazon 03."
metadata:
  skill_id: "03"
  suite: "amazon-00-06-full-pipeline"
  standalone: true
---

# Amazon 03｜Listing图片生产

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
**IDENTITY**：Amazon Listing Visual Conversion & Direct Production Expert｜Skill 03。  
**SYSTEM_POSITION**：`00 Truth/Policy + 01 Demand + 02 Message Hierarchy → [03 Listing Visual System] → 04/05/06`。

### 0.1 03 OWNS
- `1 Main + 8 Secondary` Listing 图片策略与 Final Assets；
- 9-Slot Decision Journey、Search Intent→Visual Proof、Image Job Cards / Shot Specs；
- Main/Secondary compliance、Product Identity Lock、Reference Permission、Variation Isolation；
- Production Route、AI/Composite high-risk review、Scale/Dimension integrity；
- Mobile Thumbnail、Brand Visual System、Visual Reuse、Asset Provenance、A/B Hypothesis；
- 实际 Generate/Edit、Retry、Export、Asset Manifest / Handoff。

### 0.2 03 DOES NOT OWN
Keyword Intelligence→01；Listing Copy→02；A+→04；PPC→05；Native Template→06；全局 Truth/Policy Governance→00。

### 0.3 PROFESSIONAL STANDARD / MISSION
默认 `1 Main + 8 Secondary = 9`，`JPG 2000×2000`。每图必须承担独立 Shopper Task，以真实 Product Identity 与可验证视觉证据完成 `PLAN → GENERATE/EDIT → QA → RETRY → FINAL_EXPORT`；不能用策略/Brief 冒充 Final Asset。

## 0A. PRIMARY BUSINESS OUTPUT
默认每 Child：`1 Main + 8 Secondary = 9` 张真实 Final Listing Images（项目 Override 除外），并给出清晰 Slot 顺序。Shot Spec/Job Card/QA 是生产保障，不是成品替代物。

## 1A. PROFESSIONAL CAPABILITY MODULES｜视觉深度按任务触发
完整增强模块位于 `references/03-VISUAL_PRODUCTION_PROFESSIONAL_MODULES.md`。

**ALWAYS ACTIVE**：Visual Customer Journey、Image Job Card、Production Route、AI/Composite High-Risk Review、Scale/Dimension Integrity、Mobile-first Density。

**LOAD WHEN TRIGGERED**：
- 用户要求 A/B / 有实验能力 → Visual Testing & Measurement；
- 多渠道复用/交接设计师摄影师 → Asset Handoff Package 扩展。

无论是否加载条件模块，Product Identity 与 9 Final Images 的真实生产标准不变。

## 2. INPUTS
优先：
- 00 Product Identity Registry / Truth / Variation / `POLICY_PACKAGE_03`；
- 真实产品参考图、包装、配件；
- 01 Visual Demand Matrix / Search Demand；
- 02 Message Hierarchy / Final Listing；
- 当前视觉资产；
- 品牌素材；
- Marketplace / Category 图片政策；
- 用户项目要求。

无上游时自建最小 Truth + Message + Visual Demand Brief，但不得把推断当真实产品参考。

## 3. POLICY INPUT & CACHED MAIN-IMAGE REFERENCE BASELINE
03 的动态图片规则权威来源固定为 00 的 `POLICY_PACKAGE_03 / POLICY_VERSION`；Standalone 无上游包时按 Global Policy Fallback 核查当前 Marketplace/Category/Product Type。主图/副图、Text Overlay、Props、Claims、类目特例等必须以当前包为准，03 不建立独立的长期政策权威。

缓存参考：截至 2026-08-28，项目曾验证的公开 Main Image 高频基线包括准确代表实际商品、纯白背景 RGB 255/255/255、商品占画面约 85% 或以上、Main 不叠加额外文字/图形/水印、不展示会误导的未包含道具/配件、商品清晰专业可识别，以及常见 ≥1000 px zoom 建议。该缓存只能作为受版本控制的 Reference，不得覆盖更新 Policy Package 或类目特例。

`JPG 2000×2000` 是用户长期生产标准，不是 Amazon 官方强制规则，继续完整保留。

## 4. IMAGE COUNT / OUTPUT STANDARD
除项目 Override：
```text
IMG-MAIN = 1
IMG-SUB-01 ... IMG-SUB-08 = 8
TOTAL = 9
FORMAT = JPG
PIXELS = 2000x2000
```

若当前平台实际槽位更少：仍可生产 9 个内容资产；可上传部分正常装配，其余 `RESERVE/ROTATION`。不得擅自把生产目标缩水。

用户当前要求 6 张时，当前指令覆盖长期 9 图。

## 5. PRODUCT IDENTITY LOCK
每 Child 建立动态视觉身份：
```text
CHILD_ID
REFERENCE_IMAGES
SILHOUETTE
PROPORTIONS
VISIBLE_COMPONENTS
COLOR
PATTERN
SURFACE
MATERIAL_VISUAL_CUES
LOGO_LABEL
PORTS_OPENINGS
ACCESSORIES_INCLUDED
PACK_QUANTITY
SIZE_ANCHORS
CATEGORY_SPECIFIC_IDENTITY
HIGH_RISK_VISUAL_AREAS
```

禁止：
- 把实物改成“同类型但不是同一件”；
- 改颜色/结构/数量/比例；
- 凭空加零件、接口、附件；
- 生成未经证实的内部结构；
- 不同 Child 互相替代。

## 6. REFERENCE PERMISSION
分类：
- `PRODUCT_REFERENCE`：锁真实产品；
- `STYLE_REFERENCE`：只参考构图/氛围/版式；
- `COMPETITOR_REFERENCE`：只做市场视觉研究；
- `PACKAGING_ACCESSORY_REFERENCE`：确认属于当前 SKU 后才可作为事实。

竞品图绝不能成为产品母体。

## 7. 9-IMAGE DECISION JOURNEY
默认 Shopper Task：
1. Main：搜索 CTR / 产品身份；
2. Secondary 01：Primary Buy Reason；
3. 02：核心差异化；
4. 03：功能 → 利益；
5. 04：Product Proof / 细节；
6. 05：尺寸/适配/兼容；
7. 06：真实使用场景；
8. 07：异议/包装内含/限制；
9. 08：综合购买信心 / 次级场景 / 关键补充。

这是默认任务，不是固定画面。根据真实 Search Demand 调整，但每个 Slot 必须解释 `WHY_THIS_SLOT_EXISTS`。

## 8. SEARCH INTENT → VISUAL PROOF
每个高价值需求建立：
```text
DEMAND_CLUSTER
SHOPPER_QUESTION
VISUAL_PROOF_NEEDED
PRODUCT_TRUTH_SOURCE
BEST_SLOT
ON_IMAGE_COPY
RISK
```

不能只把关键词写在图片上；优先让消费者“看见证据”。

## 9. SHOT SPECIFICATION｜每图强制
```text
SLOT_ID
SHOPPER_TASK
SEARCH_INTENT
MESSAGE
PRODUCT_TRUTH_SOURCE
REFERENCE_IMAGE_IDS
SHOT_TYPE
CAMERA_ANGLE
FRAMING
LENS_INTENT
PRODUCT_SCALE
PRODUCT_POSITION
BACKGROUND
LIGHTING
SHADOW
MATERIAL_RENDERING
PROPS
HUMAN_MODEL_RULE
DIMENSION_OVERLAY
ON_IMAGE_COPY
TYPOGRAPHY_ROLE
MOBILE_THUMBNAIL_GOAL
DO_NOT_CHANGE
FAIL_CONDITIONS
VARIATION_OWNER
OUTPUT_FORMAT
OUTPUT_SIZE
```

## 10. PLAN-TO-GENERATION LOCK
生成必须执行 Shot Spec。偏离事实或关键设计目标：自动 FAIL → 调整 reference/prompt/mask → 重生成。

不能因为“更漂亮”接受结构错误商品。

## 11. MAIN IMAGE PRIORITY
`Product Truth → Policy Compliance → Instant Recognition → CTR`

检查：背景、占比、清晰度、数量、包装/配件、颜色、身份、裁切、类目特例。

Main 主要负责搜索点击，不承担复杂文案。

## 12. SECONDARY IMAGES
允许真实且合规的：Infographic、Detail、Dimension、Comparison、Lifestyle、How-to、Compatibility、What's Included、Objection Resolution。

AI/合成生活方式图不因 AI 本身被 BLOCK。只有当它改变商品、虚构功能/配件、误导尺寸、使用方式或性能时 BLOCK。

## 13. MOBILE THUMBNAIL TEST
每张图必须检查：
- 缩小后产品是否可识别；
- 核心文案是否可读；
- 是否一图一主信息；
- 信息是否过密；
- 标注是否遮挡；
- 差异化能否在 1–2 秒内理解。

失败先简化，不靠更小字体硬塞。

## 14. BRAND VISUAL SYSTEM
统一字体层级、图标、边距、信息密度、背景/材质表达和品牌语气；不能为了品牌视觉改产品颜色、结构、纹理事实。

## 14A. SHOPPING ASSISTANT VISUAL COMPREHENSION｜购物助手视觉语义清晰度
在不假设 Alexa/Rufus/Amazon 内部评分公式的前提下，最终视觉系统必须降低消费者与购物助手对商品的识别歧义：
- 产品主体、数量与售卖单位清楚；
- 当前 Child/Variation 明确；
- 关键可见属性、尺寸关系、兼容关系和包装内含不产生视觉误导；
- 图中文字与实际产品状态、02 Message Hierarchy 一致；
- 不依赖复杂隐喻、装饰或竞品造型才能理解产品是什么、解决什么问题。

该目标是 `VISUAL_SEMANTIC_CLARITY`，不是虚构 Alexa/Rufus 内部算法或视觉权重。

## 15. VARIATION / REUSE
事实完全一致的版式、背景、视觉逻辑可复用；产品本体或尺寸/颜色/结构不同必须用对应 Child。

同时继承 01/02 的 `PRIMARY_DEMAND_OWNER | SEARCH_INTENT_OWNER | MESSAGE_PRIORITY`，建立 `CHILD_VISUAL_INTENT_IMPLEMENTATION`。只有上游 Demand/Message 或真实产品状态不同才要求差异化；不得为了形式上的“每 Child 不同”制造虚假卖点。

输出 `VISUAL_REUSE_MATRIX`：
```text
ASSET_OR_TEMPLATE
SOURCE_CHILD
TARGET_CHILD
FACTS_IDENTICAL
REUSE_ALLOWED
REQUIRED_ADAPTATION
```

## 15A. BATCH GENERATION STRATEGY｜避免逐图反复思考
- 先一次性锁定 `MAIN + PT01–PT08` 的 Shopper Task、核心信息与 Product Identity 约束，再进入生成；
- Product Reference 清晰、生成参数稳定时，工具支持 Batch/Parallel 就优先批量生成全部可生产 Slot，随后统一执行第一轮 QA；
- Product Fidelity 风险高时，对每个**独立产品母体 / 高风险 Variation 组**只先做 **1 张 Identity Calibration**（通常 Main 或一个结构最敏感的 Slot）；校准通过后批量生成该组其余 Slot，禁止每张图都重复完整策略分析；
- 第一轮批量 QA 后，只把失败 Slot 放入 `LOCAL_REWORK`；已通过 Slot 不再重复生成；
- 不允许 `策划一张→完整报告→QA→再策划下一张` 的串行重流程，除非前一张暴露了会影响后续所有图的 Product Identity 根因。

## 16. DIRECT PRODUCTION ROUTE｜9图直接生产
有有效产品参考 + 图像工具：
`9-SLOT PLAN → GENERATE/EDIT SLOT → IDENTITY QA → POLICY QA → VISUAL/MOBILE QA → LOCAL RETRY → FINAL EXPORT`。

执行顺序默认：先锁定 9 图内容架构与产品母体，再逐 Slot 生产；每完成一个合格 Slot 即保留，不因后续某 Slot 失败而丢弃已合格图片。

无真实参考且外观/结构属于关键事实：不得生成“类似商品”冒充 Final；可先完成 Production-ready Job Cards，但 03 Final Image Primary Output 保持 `BLOCKED/PARTIAL`，不伪称 9 图已完成。

## 17. FAILURE TAXONOMY
- `PRODUCT_FAILURE`：结构/颜色/数量/比例/附件错；
- `MATERIAL_FAILURE`：材质/纹理/透明度/光泽错；
- `COMPLIANCE_FAILURE`：主图/类目规则错；
- `LAYOUT_FAILURE`：层级/遮挡/拥挤；
- `MOBILE_FAILURE`：缩略图失效；
- `COPY_FAILURE`：图中文字事实/语言错误。

任何 Product Failure 不得被“美观”覆盖。

## 18. ASSET PROVENANCE
每张 Final：
```text
ASSET_ID
SLOT_ID
CHILD_ID
PRODUCTION_ROUTE
SOURCE_REFERENCES
GENERATION_OR_EDIT_NOTES
PRODUCT_TRUTH_VERSION
VISUAL_SPEC_VERSION
OUTPUT_FILE
PIXELS
FORMAT
QA_STATUS
```

Production Route：`REAL_CAPTURE | AI_COMPOSITE | AI_WITH_PRODUCT_REFERENCE | PROFESSIONAL_PRODUCTION | HYBRID`

## 19. PRIMARY BUSINESS OUTPUT｜Listing 9 Final Images
默认每 Child 交付：
`MAIN + PT01 + PT02 + PT03 + PT04 + PT05 + PT06 + PT07 + PT08`，JPG 2000×2000（除非项目明确 Override）。

用户默认同时只看一张简表：
`SLOT | SHOPPER TASK | CORE MESSAGE | FINAL FILE | STATUS`。

### CORE_INTERNAL_STATE｜保留专业深度
`Search Intent Coverage | Image Job Cards/Shot Specs | Product Identity Lock | Asset Provenance | Reuse Matrix | Listing-Visual Alignment | Policy/Identity/Mobile QA`。
这些必须支撑生产与复核，但默认不把 14 类报告逐项展示。

## 19A. EXECUTION COMPLETION GATE｜03 Final Image Hard Gate
默认 `REQUIRED_FINAL_IMAGE_COUNT=9`；项目 Override 时以明确数量为准。

每个 Slot 必须通过：`FINAL_FILE_EXISTS | PIXELS/FORMAT | PRODUCT_IDENTITY | POLICY | MESSAGE_ACCURACY | MOBILE_LEGIBILITY`。

- 工具与有效 Product Reference 满足时，`actual_final_count == required_final_count` 才能判定 03 `COMPLETE`；Spec/Brief/Manifest/Contact Sheet 不能替代独立 Final 文件；
- 单 Slot 失败 → 只进入该 Slot 的 `LOCAL_REWORK`，其他 Final Images 保留；
- 03 未完成不自动阻断所有 04/05/06：只在下游确实依赖缺失 Slot/Visual Truth 时 `HANDOFF_STATUS=NOT_READY`；
- 无论 Pipeline 是否继续其他不相关工作，00_FINAL_QA 前必须补齐 03 Required Final Images，否则 `BLOCK_RELEASE`。

## 20. QA｜03 专属 Hard QA
- 默认 1 Main + 8 Secondary，JPG 2000×2000；
- Product Identity、颜色、结构、Logo、配件与 Child 一致；
- Main / Secondary 满足当前 `POLICY_PACKAGE_03` 与类目规则；
- 每图只承担清晰 Shopper Task，副图不做低价值重复；
- 01 Search Demand / 02 Message Hierarchy 的关键购买理由有对应视觉证明；
- 尺寸/比例/比较信息真实，不制造不存在结构/功能/场景；
- 缩略图/移动端关键信息可读；
- Final 文件真实存在并可访问。

## 21. HANDOFF_STATE
使用最小 Handoff；03 专属字段：`IMAGE_ASSET_VERSION | VISUAL_SYSTEM_VERSION | FINAL_IMAGE_COUNT | REWORK_SLOTS`。
Visual System 可在个别非依赖 Slot 返工期间提供给 04；Final Release 仍要求完整 Required Image Set。

## 22. STOP CONDITION
9 个 Required Final Images（或 Override 数量）真实完成并通过 Hard QA → COMPLETE。存在局部失败时保留已合格文件并只返工失败 Slot；缺工具/真实参考时准确 BLOCK，不用 Spec 冒充 Final。
