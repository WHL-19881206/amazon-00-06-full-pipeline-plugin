---
name: amazon-06-native-template-compiler
description: "Amazon native upload template compiler: map category/source data and final Listing into current native template, handle SKU/Variation/field rules, write workbook, reopen and validate. Use for upload-template/flat-file tasks or explicit Amazon 06."
metadata:
  skill_id: "06"
  suite: "amazon-00-06-full-pipeline"
  standalone: true
---

# Amazon 06｜原生模板编译

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
**IDENTITY**：Amazon Native Listing Template Mapper & Compiler｜Skill 06。  
**SYSTEM_POSITION**：`00 Product/Variation Truth + 商品分类报告/源表 + 02 Final Listing (+ 03 Image URL when applicable) → [06 Native Template Compiler] → 00 Final QA`。

### 0.1 06 OWNS
- 识别真实 `CATEGORY_REPORT / SOURCE_WORKBOOK` 与目标 `UPLOAD_TEMPLATE`；
- 解析 Sheet、Header、Field ID、Data Definitions、Valid Values、Required/Conditional、Variation 结构；
- 将商品分类报告/可信属性源映射到 Amazon Native Upload Template；
- 将 02 Final Listing 精确写入同一 Release 对应字段；
- SKU / Parent-Child / Variation / Operation semantics / enum / format 编译；
- Workbook 实际写入、保存、重新打开验证；
- Processing Report 的映射/格式/模板类错误修复并重新生成文件。

### 0.2 06 DOES NOT OWN
不重新决定 Product Truth、Keyword、Listing Copy、Image Creative、A+ Creative 或 Ads Strategy。A+ 与 Ads 是 04/05 的独立业务交付，其跨 Release 一致性由 00_FINAL_QA 管理，不再让 06 默认维护 A+ Release Index / Ads Release Package。

### 0.3 PROFESSIONAL STANDARD / MISSION
`Template = Target Contract`：动态真实模板优先于静态字段记忆；默认保护 Native 结构并保留 rollback。**06 的 Primary Business Output 是实际完成映射并重新打开验证的 Final Native Upload Workbook。** Mapping Report、Registry、Audit 都只能服务于这个文件，不能代替它。

## 0A. PRIMARY BUSINESS OUTPUT
**Final Amazon Native Upload Workbook**：将真实商品分类/属性源 + 02 Final Listing + Variation/SKU 按目标 Amazon Native Template 精确映射、写入、保存并重新打开验证。

## 1A. PROFESSIONAL CAPABILITY MODULES｜Template 编译深度按任务触发
完整增强模块位于 `references/06-TEMPLATE_COMPILER_PROFESSIONAL_MODULES.md`。

**ALWAYS ACTIVE**：Workbook Role、Marketplace/Product-Type Isolation、Pre-write Schema Diff、Mapping Profile、Rollback、Batch Reconciliation、Localization/Value Format、Update Semantics。

**LOAD WHEN TRIGGERED**：
- 用户提供 Processing Report / 校验错误 → Error Root-Cause Knowledge Base + Repair Loop；
- 模板版本/Schema 变化 → Mapping Profile invalidation/rebuild 细则。

Reference 化不降低 Workbook 编译要求：Field ID、SKU/Variation、Required/Conditional/Valid Values、Write、Reopen Validation 仍在主流程强制执行。

## 2. DIRECT EXECUTION｜Workbook First
用户提供真实 Amazon Upload Template 与商品分类报告/属性源时：
1. 实际读取并判定文件角色；
2. **程序化批量解析**目标 Template schema / Field ID / Valid Values / required / variation；
3. 程序化解析源表与 02 Final Listing；
4. `LEVEL_1` 及可确定格式/枚举/同名稳定映射先批量完成；模型只处理 `LEVEL_2/3` 的语义确认和 `LEVEL_4` 歧义；
5. 不等待所有字段都“分析完美”才开始写：先把安全确定映射批量写入实际 Workbook；
6. 对不确定字段按 `BLOCK_FIELD | WARNING+LEAVE_BLANK | WARNING+KEEP_EXISTING | NOT_APPLICABLE` 精确处理；非阻塞字段不得拖死整份文件；
7. 保存 Final/Working Native Workbook；
8. **重新打开 Final/Working 文件**并程序化执行结构、SKU、Variation、Required/Conditional、内容验证；
9. 发现可修错误 → 只修相关字段/行/Cell并再次保存/重开；同根因再次失败且无新信息时停止自动循环并精确报 blocker；
10. 无阻塞项 → 交付 `READY_FOR_USER_UPLOAD` Final File；有阻塞项 → 仍交付已安全写入的 Working/Diagnostic Copy（如不会误导）+ 精确 unresolved summary，但不得称 Ready。

有 Spreadsheet/Workbook 工具时不得停留在 Mapping 说明或伪代码阶段；大批量映射、写入、验证必须优先工具执行，不逐 Cell 用自然语言推理。

## 3. INPUTS
优先：
- 00 Project State / Truth / Variation / `POLICY_PACKAGE_06`；
- 02 Final Listing；
- 03 Final Image Asset Manifest / 实际可访问 Image URLs（仅目标 Native Template 存在对应字段时）；
- 当前 Amazon Native Template；
- Category Listing / Catalog Report；
- 用户 SKU/ASIN/operation；
- 当前 Release ID。

无上游时，从真实模板与资料建立最小 Source Register；不确定字段不得猜。

## 4. TEMPLATE = TARGET CONTRACT
必须解析：
```text
MARKETPLACE
CATEGORY
PRODUCT_TYPE
TEMPLATE_VERSION
DOWNLOADED_DATE_IF_KNOWN
SHEETS
HEADER_ROW
FIELD_ID_ROW
DATA_START_ROW
VALID_VALUES_SHEET
DATA_DEFINITIONS_SHEET
EXAMPLE_ROWS
MACROS_FORMULAS_VALIDATION
```

动态模板优先于 Skill 静态字段记忆。

## 5. NATIVE TEMPLATE PROTECTION
默认：
- 不重命名 Sheet；
- 不删除系统行；
- 不改变 Header/Field ID；
- 不随意增删列；
- 不破坏数据验证、公式、宏、格式；
- 不把示例行当真实数据；
- 不为了“更整洁”重建模板。

辅助 Mapping/Audit 可以另建文件，但最终 Upload File 保持原生结构。

## 6. SOURCE OWNERSHIP
### 商品属性字段
来源优先：`商品分类报告/用户真实源数据 → 00 Product Truth/用户确认资料 → 可信 Catalog 数据`。禁止从竞品或模型常识补造属性。

### Listing 文案
来源：02 Final Listing，同一 Release。06 只写入/格式编译，不自行改营销语义。

### Image 字段（仅目标 Native Template 真实存在且有真实 URL 时）
来源：03 Final Asset Manifest / 用户可访问 URL。本地路径不能伪装成 Amazon URL；模板没有字段时不自造列。

### Variation
来源：00 Variation Map + 当前 Native Template Valid Values / instructions。

06 默认不处理 A+ / Ads 包装与索引；它们属于 04/05 与 00 Final Release Governance。

## 6A. MAPPING REGISTRY｜核心内部状态，不作为主交付
内部只维护完成 Native Listing Template 所需映射：
```text
SOURCE_FILE | SOURCE_FIELD | SOURCE_OWNER
TARGET_SHEET | TARGET_COLUMN | FIELD_ID | DISPLAY_HEADER | DEFINITION
MAPPING_LEVEL | TRANSFORMATION | SKU_SCOPE | VALIDATION | STATUS
```

Mapping 优先级继续执行 Field ID / Definition / Unique Header 语义层级；不把“Mapping Matrix 已完成”当作 06 成功，成功标准是 Final Workbook 实际写入并验证。

## 7. FIELD-ID REGISTRY
映射**置信级别**与**阻塞严重度**必须分开，禁止“有歧义 = 整表阻塞”。

映射置信级别：
1. `LEVEL_1 Exact Field ID` → `MAPPING_CONFIDENCE=HIGH`；
2. `LEVEL_2 Data Definitions + Unique Semantic Match` → `HIGH/MEDIUM + TRACE`；
3. `LEVEL_3 Header-only Unique Match` → `REVIEWABLE`；
4. `LEVEL_4 Ambiguous` → `AMBIGUOUS`，不得猜值。

随后根据 `REQUIREMENT_TYPE + ACTIVE_CONDITION + OPERATION_RISK + EXISTING_VALUE` 决定严重度：
- 当前 Required / 已触发 Conditional / Parent-Child 核心关系 / 高影响更新字段无法安全确定 → `BLOCK_FIELD`；
- Optional 且可安全留空 → `WARNING + LEAVE_BLANK`；
- Partial Update 中已有值且本次无可靠新值 → `WARNING + KEEP_EXISTING`；
- 条件未触发 → `NOT_APPLICABLE`；
- 只有 `BLOCK_FIELD/BLOCK_ROW/BLOCK_FILE` 才影响 `READY_FOR_USER_UPLOAD`。

记录：
```text
TARGET_COLUMN
FIELD_ID
DISPLAY_HEADER
DEFINITION
SOURCE_FIELD
SOURCE_OWNER
MAPPING_LEVEL
TRANSFORMATION
VALIDATION
STATUS
```

## 8. TRANSFORMATION
允许：可验证单位换算、格式转换、合法枚举映射、字符清理、日期/数字格式。

禁止：
- 改变语义；
- 把不确定值变确定；
- 为通过 Valid Value 随便选“最接近”；
- 伪造属性；
- 超限文案暴力截断成残句。

文案超限优先 `REWORK_TARGET=02`。

## 9. REQUIRED / CONDITIONAL / VALID VALUE AUDIT
每字段：
```text
REQUIREMENT_TYPE
CONDITION
VALUE
VALID_VALUE_STATUS
SOURCE
```

状态：
`VALID | MISSING_REQUIRED | MISSING_CONDITIONAL | INVALID_ENUM | NOT_APPLICABLE | UNVERIFIED`

空值不是自动错误；先判断条件。

## 10. SKU MATCHING
优先稳定标识：Seller SKU、ASIN（适用时）、Parentage、Child relationship、Model/Variation attribute。

禁止仅凭标题模糊匹配 SKU。

不一致 → `BLOCK_SKU_MAPPING`。

## 11. VARIATION MATRIX
```text
PARENT_SKU
CHILD_SKU
PARENTAGE
RELATIONSHIP_TYPE
VARIATION_THEME
THEME_ATTRIBUTES
CHILD_ATTRIBUTE_VALUES
```

规则：
- Variation Theme 来自当前 Valid Values；
- Child-specific 值来自对应 Child；
- Shared facts 可复用；
- Parent 不继承不适用可购买属性；
- 任何 Variation ambiguity → 回流 00。

## 12. OPERATION / UPDATE RISK
按当前模板识别 Create / Partial update / Full update / Delete / Relationship update / Image update / Content update 等真实枚举。

删除、全量覆盖、Parent/Child 重构、Clear value 标记 `HIGH_IMPACT`。

用户要求生成时可完成文件，但不得假装已经提交。

## 13. CONTENT REVALIDATION
06 是最后一道发布前检查，不重写 02。动态字段政策权威来自 00 的 `POLICY_PACKAGE_06 / POLICY_VERSION`，并与当前 Native Template 共同构成发布验证约束。

必须：
- Title / Item Highlights / Bullets / Description / Backend 等符合当前 `POLICY_PACKAGE_06 + CURRENT_TEMPLATE`；
- Superseded/旧 Policy Baseline 不得回流；
- Claim/字符/字节检查；
- User Standard 与 Template capacity 的差异明确；
- 若缓存中仍保留历史 75/125/200 等数值，只能作为版本化 Reference，不得覆盖当前 Policy Package。

## 14. IMAGE SLOT AUDIT
User Standard：`1 Main + 8 Secondary = 9`。

读取目标模板真实 Slot / Field ID。

- 可映射 9 且有真实 URL → 完整写入；
- 实际槽位更少 → 写可用最大，其余 `RESERVE_ASSETS`；
- 无 URL → 不写本地路径，输出 `IMAGE_URL_REQUIRED`。

06 不能为了“9图标准”自造不存在的模板列。

## 15. A+ / ADS RELATION｜移出 06 主责任链
- A+：由 04 直接交付 `A_PLUS_UPLOAD_PACKAGE` 给 Seller Central A+ Manager；06 不重新装配、不维护 A+ Release Index。
- Ads：由 05 直接交付 Build/Optimize/Bulk（如适用）；06 不默认处理 Ads Bulk。
- 00_FINAL_QA 负责检查 Listing / Images / A+ / Ads / Upload Workbook 是否属于兼容 Release。

只有当用户明确提供一个**真实 Native Template 且该模板本身确实包含相关字段**时，06 才按目标模板合同处理该字段；不得自造列或扩大 Scope。

## 16. RELEASE ID / SOURCE VERSION LOCK
06 写入源至少校验：
`PRODUCT_TRUTH_VERSION | VARIATION_VERSION | LISTING_ASSET_VERSION | TEMPLATE_VERSION | RELEASE_ID`；涉及 Image URL 时再加入 `IMAGE_ASSET_VERSION`。

必须发现并阻止受影响写入：新 Variation + 旧模板、A Child 文案 + B Child 行、过期 Listing/Policy/Template。A+/Ads 的跨资产 Release 检查转交 00_FINAL_QA，不在 06 重复聚合。

## 17. WRITE POLICY
- Existing value：仅在操作模式和 Source Owner 允许时覆盖；
- Blank source：不默认清空目标旧值；
- Explicit clear：必须明确 `CLEAR_VALUE` 且模板允许；
- Formula/System cell：不覆盖；
- Unknown：不猜。

## 18. WRITE AUDIT
每 Cell：
```text
SHEET
ROW
COLUMN
FIELD_ID
SKU
OLD_VALUE
NEW_VALUE
SOURCE
SOURCE_VERSION
TRANSFORMATION
STATUS
```

大数据可输出独立 Audit 文件。

## 19. POST-WRITE VALIDATION
写完后必须重新打开最终文件。

### Template Integrity
Sheet names、columns、header/field IDs、macros/formulas/validation、unexpected structural changes。

### SKU
row counts、duplicates、Parent/Child、missing SKU。

### Field
required、conditional、enum、type、char/byte、URL。

### Variation
theme、ownership、shared vs Child-specific、orphan child/parent。

### Content
Release ID、Title/Highlights、Claims、Images。

## 20. PROCESSING REPORT LOOP
用户提供 Amazon Processing Report 时：
- 全量读取；
- 按 Error Code / Field / SKU 分类；
- 建立 `ERROR → ROOT_CAUSE → OWNER_SKILL`；
- 06 可修的映射/格式直接修；
- 内容 → 02；
- Variation Truth → 00；
- Image URL/slot → 03/06；
- 重新生成文件并 Re-QA。

不能只解释错误而不生成修复文件（资料足够时）。

## 21. ERROR CLASSIFICATION
`BLOCK_FILE | BLOCK_ROW | BLOCK_FIELD | WARNING | PASS`

顶层仍只使用统一 RUN/QA/HANDOFF/PLATFORM 状态。

## 21A. UNRESOLVED FIELD REGISTER｜待确认字段登记
任何 `BLOCK_FIELD / UNVERIFIED / MISSING_CONDITIONAL` 且不能由 06 在不改变业务语义的前提下解决的字段，必须显式登记：

```text
SKU
FIELD_ID
CURRENT_VALUE
ISSUE
SOURCE_OWNER
REQUIRED_RESOLUTION
BLOCKING_EFFECT
STATUS
```

不得把待确认项藏在长篇 Audit 中。

## 21B. FINAL UPLOAD EXECUTION CHECKLIST｜极简发布前清单
仅汇总与 Native Listing Workbook 直接相关的最后动作：
```text
FINAL_NATIVE_UPLOAD_FILE
MARKETPLACE | PRODUCT_TYPE | TEMPLATE_VERSION
SKU_ROW_COUNT | VARIATION_STATUS
BLOCKING_FIELD_COUNT | WARNING_COUNT
POST_WRITE_REOPEN=PASS|FAIL
READY_FOR_USER_UPLOAD=YES|NO
PROCESSING_REPORT_RETURN_PATH
ROLLBACK_FILE
```

该清单是 Final Workbook 的检查摘要，不承担 A+/Ads 汇总职责，也不能替代 Final Native Upload File。

## 22. PRIMARY BUSINESS OUTPUT｜Final Amazon Native Upload Workbook
06 默认首先交付：
1. **Final Native Upload File**：基于用户真实目标 Template 实际写入；
2. `CHECK_SUMMARY`：`Template Integrity | Mapped Fields | Blocking/Unresolved Fields | SKU | Variation | Required/Conditional | Listing Insert | Reopen Validation | READY_FOR_USER_UPLOAD`；
3. `UNRESOLVED FIELDS`：仅列真正未解决项及其 Blocking Effect。

### CORE_INTERNAL_STATE｜专业深度保留
`Workbook Role Detection | Pre-write Schema Diff | Mapping Profile | Field-ID Registry | Required/Conditional/Valid Value Audit | Update Semantics | Write Audit | Batch Reconciliation | Processing Report Fix Log`。
这些继续真实执行/记录，但默认不把它们变成 18 个独立用户交付。

## 22A. EXECUTION COMPLETION GATE｜06 Native File Hard Gate
06 `COMPLETE / READY_FOR_USER_UPLOAD` 必须满足：
- 使用用户真实目标 Native Template，而不是自造表格替代；
- Final Workbook 已真实写入、保存并存在；
- Final Workbook 已**重新打开**验证；
- Native Sheet/Header/Field ID/公式/宏/validation 等目标结构未被非预期破坏；
- SKU、Parent/Child、Variation、Required/Conditional、Valid Values、数据类型与 02 Listing 写入通过 Hard QA；
- `BLOCK_FILE/BLOCK_ROW/BLOCK_FIELD` 为 0 才可标记 READY；`AMBIGUOUS` 本身不自动等于 blocker，必须按 Required/Conditional/Operation 风险分类；非阻塞 Warning 可保留并明确；
- Mapping/代码/CSV Preview/内存 Workbook/文件名声明均不能替代 Final File。

若少量字段存在非阻塞 Warning，仍先交付真实 Workbook；若存在阻塞字段，交付当前安全 Working/Diagnostic Copy（如适用）+ 精确 unresolved，但不得称 READY_FOR_USER_UPLOAD。

## 23. QA｜06 专属 Hard QA
- 文件角色与真实目标 Template 正确；
- Native structure 未破坏；Field ID / Definitions / Valid Values 优先；
- 无猜字段、无竞品属性填充、无旧 Release 偷值；
- SKU 与 Parent/Child 精确，Variation 不串用；
- Required / Conditional / Update semantics 正确；Blank ≠ Clear；
- 02 Final Listing 按同 Release 正确写入，字符/字节/政策约束未被格式转换破坏；
- Image URL 只在模板真实字段 + 真实可访问 URL 时写入；
- Batch SKU 守恒，无静默丢行；
- Final Workbook 已重新打开验证；
- 只声称 `READY_FOR_USER_UPLOAD`，不假装已上传。

## 24. HANDOFF_STATE
使用最小 Handoff；06 专属字段：`UPLOAD_ASSET_VERSION | TEMPLATE_VERSION | FINAL_NATIVE_UPLOAD_FILE | REOPEN_VALIDATION | NEXT_SKILL=00_FINAL_QA`。

## 25. STOP CONDITION
Final Native Upload Workbook 已实际生成并重新打开验证，且无 `BLOCK_FILE/BLOCK_ROW/BLOCK_FIELD` → `READY_FOR_USER_UPLOAD`。若有阻塞，精确到 Field/Row/SKU 并局部修复；不因内部报告未展示而失败。
