# Reference｜Skill 00 Professional Capability Modules

> 从业务深度保留版主 Runtime 迁移。此文件不是“被删除内容”；当主 Skill 的 LOAD WHEN TRIGGERED 条件成立时必须读取并执行。ALWAYS ACTIVE 要点已在主 Runtime 摘要保留。

## 1A. PROFESSIONAL CAPABILITY ENHANCEMENT｜治理专业能力增强


### 1A.1 EVIDENCE BOUNDARY｜证据边界三分法
除既有 `FACT_STATUS` 外，00 对项目级判断增加证据用途标签：
- `CONFIRMED`：用户真实资料、官方/账户/模板数据或已检查证据直接支持；
- `DIRECTIONAL`：基于明确假设、代理指标、估算或跨数据推导，可用于规划但不能当事实；
- `UNRESOLVED`：必须由 Seller Central、当前官方来源、用户文件、实验/检测、第三方专业机构或其他权威证据解决。

任何 `DIRECTIONAL/UNRESOLVED` 结论不得偷偷升级为 `VERIFIED Product Truth`。

### 1A.2 MARKETPLACE TRANSFER FIREWALL
跨站点时默认禁止以下“自动继承”：
- 一个 Marketplace 的政策直接套到另一个 Marketplace；
- US Search Demand / Keyword Volume 直接当作 DE/JP/UK 等本地需求；
- 一个站点可售/可上架推定另一个站点也可售；
- 一个站点的 Variation Theme、A+ entitlement、Ads feature、Template field、Review/Brand benefit 推定另一个站点完全相同；
- 英文 Listing 机械翻译后视为本地化完成。

00 必须建立 `MARKETPLACE_TRANSFER_CHECK`：`POLICY | PRODUCT_ELIGIBILITY | LOCALIZATION | UNITS | POWER/PLUG | LABEL/WARNING | ACCOUNT_FEATURE | TEMPLATE | ADS_FEATURE | VARIATION`。

### 1A.3 CATEGORY / REGULATORY RISK RESOLVER
当 Product Type 触发高风险域时，00 必须识别但不得冒充法律/税务/认证顾问：
`BATTERY_DG | CHEMICAL | COSMETIC | FOOD | SUPPLEMENT | MEDICAL_HEALTH | CHILDREN | RADIO_WIRELESS | PPE_SAFETY | FOOD_CONTACT | TEXTILE_LABEL | ELECTRICAL | ENVIRONMENTAL_EPR | OTHER_CATEGORY_SPECIFIC`。

对每一风险项建立：
```text
RISK_DOMAIN
TRIGGER_FACT
MARKETPLACE
CURRENT_EVIDENCE
REQUIRED_OFFICIAL_OR_PROFESSIONAL_SOURCE
AFFECTED_SURFACE
GATE_DECISION
OWNER
```

`GATE_DECISION` 只表达当前治理结论：`PASS | HOLD_FOR_VERIFICATION | BLOCK_CONFLICTING_ACTION`，不取代顶层 RUN/QA/HANDOFF 状态。

### 1A.4 LOCALIZATION GOVERNANCE
跨站点内容不仅检查语言，还检查：
- native search wording / category terminology；
- measurement units、decimal/number formatting；
- voltage/plug/compatibility（适用时）；
- label/warning/language requirement；
- locally relevant use cases / seasonality；
- claim meaning after localization；
- 目标站点 Template / Browse / Variation 适用性。

00 只负责建立约束与确认状态；实际关键词本地化由 01，Listing 由 02，视觉由 03/04，模板由 06 完成。

### 1A.5 HARD-GATE REGISTER
所有会改变“能否继续发布/投放/生产”的问题必须进入统一 Gate：
```text
GATE_ID
GATE_TYPE
TRIGGER
EVIDENCE
AFFECTED_SKILLS
AFFECTED_SKUS
CAN_CONTINUE_SAFE_WORK
REQUIRED_RESOLUTION
OWNER_SKILL_OR_USER
STATUS
```

原则：**只阻塞真正受影响的动作，不把一个局部未知扩大为全项目停止。**
