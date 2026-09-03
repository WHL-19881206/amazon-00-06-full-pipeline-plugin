# Reference｜Skill 03 Professional Capability Modules

> 从业务深度保留版主 Runtime 迁移。此文件不是“被删除内容”；当主 Skill 的 LOAD WHEN TRIGGERED 条件成立时必须读取并执行。ALWAYS ACTIVE 要点已在主 Runtime 摘要保留。

## 1A. PROFESSIONAL CAPABILITY ENHANCEMENT｜视觉策略与生产专业增强

### 1A.1 VISUAL CUSTOMER-JOURNEY RESEARCH
九图规划前，除现有 Search Intent 外增加四类视觉判断：
- `FIRST_IMPRESSION`：搜索页/首屏 1–3 秒能否识别产品、数量、核心差异；
- `DECISION_FACTOR`：买家真正比较哪些属性；
- `TRUST_REQUIREMENT`：什么细节/尺寸/结构/材质/包装证据能降低风险；
- `OBJECTION`：买前最担心什么，哪一张图负责消除。

竞品视觉研究只能回答：市场共性、头部视觉惯例、信息缺口、差异化机会；竞品产品造型与事实绝不能进入我方母体。

### 1A.2 IMAGE JOB CARD｜每张图的完整生产任务
在现有 Shot Spec 基础上，每图补充：
```text
SHOPPER_QUESTION
DECISION_TO_ENABLE
REQUIRED_SOURCE_ASSETS
VISIBLE_PRODUCT_STATE
CROP
NEGATIVE_SPACE
PROP_PERMISSION
MODEL_DIRECTION
TEXT_SAFE_AREA
FIDELITY_RISK
COMPLIANCE_RISK
FILENAME
A_B_TEST_HYPOTHESIS_IF_ANY
```

这样图片不仅描述“画什么”，还明确“为什么画、帮助消费者做什么决定、哪些素材必须真实存在”。

### 1A.3 PRODUCTION ROUTE DECISION
按事实敏感度与现有素材选择：
- `REAL_CAPTURE`：Main、纹理/细节/颜色/fit 等高度真实性敏感；
- `AI_WITH_PRODUCT_REFERENCE`：产品母体稳定、需要场景扩展；
- `AI_COMPOSITE`：真实产品抠图 + 可控背景/信息图；
- `PROFESSIONAL_PRODUCTION`：复杂 model shot、多 SKU、受监管/fit/texture 敏感；
- `HYBRID`：真实 Hero/Detail + AI 场景/图形。

选择依据必须记录，不默认 AI 或真人摄影永远更优。

### 1A.4 AI / COMPOSITE HIGH-RISK REVIEW
除产品轮廓外，重点检查：
`hands | fingers | reflections | shadows | transparency | glass | screens | ports | seams | labels | packaging copy | logo | small accessories | repeated parts | count | texture | edge geometry`。

这些区域即使整体“看起来像”也可能造成事实错误，必须放大审查。

### 1A.5 SCALE / DIMENSION / COMPARISON INTEGRITY
- Scale reference 必须与真实尺寸关系一致；
- Dimension line / arrow / unit 不得遮挡或产生错误测量起点；
- Human/model 比例不得暗示错误尺寸；
- Comparison 只能比较真实、可验证、同口径属性；
- 不使用无法证明的“ours vs competitors: better/stronger/best”；
- 如果只能做 generic alternative，应确保对比对象定义清楚且不误导。

### 1A.6 MOBILE-FIRST INFORMATION DENSITY
每张副图优先一个主信息。移动端检查不仅看字体大小，还看：
- 1–2 秒是否理解主结论；
- 产品是否仍为视觉主角；
- 重要数字/单位是否可辨；
- 图标是否需要阅读说明才能理解；
- 文案缩小后是否导致信息层级倒置。

失败处理顺序：`删次要信息 → 强化层级 → 放大证据 → 最后才考虑增加文字密度`。

### 1A.7 VISUAL TESTING & MEASUREMENT
提出 A/B 测试时必须先写 Hypothesis：
`VARIABLE | WHY | EXPECTED_SHOPPER_BEHAVIOR | PRIMARY_METRIC | GUARDRAIL | TEST_WINDOW | DECISION_RULE`。

主图优先看 CTR 与下游 CVR guardrail；副图更关注 CVR/return/QA themes 等可获得指标。禁止无实验依据声称“这张图会提升 X% 转化”。

### 1A.8 ASSET HANDOFF PACKAGE
每 Child Final 除 Asset Manifest 外增加：
- Final filename convention；
- source/reference IDs；
- captured/composited/generated route；
- revision/version；
- 2000×2000 JPG export QA；
- text/copy proofread；
- mobile preview result；
- reserve/rotation asset（如有）；
- 交给 04/06 的可复用范围。
