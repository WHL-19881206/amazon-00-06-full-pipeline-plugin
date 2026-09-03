# Reference｜Skill 01 Professional Capability Modules

> 从业务深度保留版主 Runtime 迁移。此文件不是“被删除内容”；当主 Skill 的 LOAD WHEN TRIGGERED 条件成立时必须读取并执行。ALWAYS ACTIVE 要点已在主 Runtime 摘要保留。

## 1A. PROFESSIONAL CAPABILITY ENHANCEMENT｜搜索需求与关键词专业增强

### 1A.1 MULTI-SOURCE DEMAND INTELLIGENCE
01 不只读取“关键词 + 搜索量”。当数据存在时，必须把不同来源转成不同类型的需求证据：
- **ABA / Search Analytics / SQP / Brand Analytics**：搜索频率、query funnel、click/cart/purchase/conversion share、ASIN 表现等；
- **PPC Search Term**：真实付费触发词、CTR/CVR/Orders/ACoS 与增量发现；
- **Business Report**：Session / Unit Session / sales context，用于判断流量质量与 Listing 承接；
- **Amazon Autocomplete**：真实搜索表达候选与长尾发现，但默认是 `CANDIDATE_DEMAND_SIGNAL`，不是搜索量；
- **Review / Q&A**：消费者语言、抱怨、疑虑、Feature Request、使用场景；
- **Item Comparison / Alternate Purchase / competitor evidence**：消费者考虑集、切换触发与替代关系；
- **Market Basket（存在时）**：共购/相邻需求与 Cross-sell 线索，不自动升级为本产品关键词；
- **Rank / Indexing / Search visibility（存在时）**：验证“有需求但未获得正确曝光”还是“有曝光但 CTR/CVR 弱”。

来源之间不能机械相加。必须先解释 metric grain 与业务含义，再进入 Demand Cluster。

### 1A.2 SEARCH FUNNEL GAP DIAGNOSIS
对有 SQP/Brand Analytics 或同类漏斗数据的 Query，至少判断：
```text
DEMAND_PRESENT?
IMPRESSION_GAP?
CLICK_SHARE_GAP?
CART_GAP?
PURCHASE_SHARE_GAP?
CTR_PROBLEM?
CVR_PROBLEM?
LISTING_COVERAGE_GAP?
PRODUCT_FIT_GAP?
AD_DISCOVERY_GAP?
```

典型解释：
- Demand 强 + Impression 弱 → 先查 Relevance / indexing / category / ads coverage；
- Impression 足 + Click 弱 → 可能是主图/Title/Price/Review/意图错配，交给 02/03/05；
- Click 足 + Purchase 弱 → 可能是 CVR/产品匹配/价格/异议问题，交给 02/03/04；
- Conversion 强但流量小 → 可能属于值得扩展的精准需求。

禁止伪造所谓 A9/A10/Rufus 固定权重。

### 1A.3 CUSTOMER VOICE & REVIEW INTELLIGENCE
Review/Q&A 分析至少区分：
- Positive theme；
- Negative theme；
- Complaint frequency；
- Complaint severity / return trigger；
- Usability vs quality vs expectation gap；
- Feature request；
- Alternative/competitor mention；
- Switching trigger；
- 原话中的本地消费者表达。

每条洞察保留 `SOURCE / SAMPLE_SCOPE / RECENCY / FREQUENCY_IF_KNOWN / EVIDENCE_CONFIDENCE`。没有全量 Review 时不能把样本频率伪装成市场总体比例。

### 1A.4 CHILD KEYWORD PORTFOLIO｜恢复并强化每 Child 专业词库
只要存在 Variation，每个 Child 除 `SHARED_PARENT_CORE` 外必须独立输出：
1. `TRAFFIC_KEYWORDS`：相关但较宽，负责正确曝光扩展；
2. `CONVERSION_KEYWORDS`：属性/意图与 Child 高度匹配；
3. `BROAD_DISCOVERY_KEYWORDS`：适合测试与发现，但需要更严的相关性控制；
4. `LONG_TAIL_ATTRIBUTE_KEYWORDS`：Size/Color/Material/Style/Use Case/Audience/Compatibility 等精准组合。

每个词同时标记：`KEYWORD_ROLE | KW_TIER | CHILD_OWNER | RELEVANCE | INTENT | ELIGIBILITY | RECOMMENDED_SURFACE | EVIDENCE_SOURCE`。

### 1A.5 KEYWORD LIFECYCLE PORTFOLIO
每 Child 建立：
`ACTIVE | TEST | RESERVE | HOLD | EXCLUDE`

至少记录：
```text
FIRST_SEEN
LAST_VALIDATED
VALIDATION_SOURCE
MARKETPLACE
LIFECYCLE_STATUS
WHY
NEXT_REVIEW_TRIGGER
```

新词、Autocomplete、AI/Web 候选未经真实验证不得直接进入 ACTIVE。

### 1A.5A DISCOVERY EXPANSION REGISTER｜AI / Web / Autocomplete 候选扩展登记
AI、Web、Autocomplete、竞品与 Review/Q&A 可以扩大候选词发现范围，但 Discovery 不等于已验证 Amazon Search Demand。所有新候选必须进入独立登记，未经真实数据、用户事实或可验证市场证据确认，不得直接晋级 `ACTIVE`、KW-T1/T2 或核心部署。

```text
CANDIDATE_TERM
DISCOVERY_SOURCE
DISCOVERY_METHOD=AI|WEB|AUTOCOMPLETE|COMPETITOR|REVIEW_QA
MARKETPLACE
INITIAL_INTENT
PRODUCT_TRUTH_ELIGIBILITY
VALIDATION_SOURCE
VALIDATION_STATUS=UNVALIDATED|PARTIALLY_VALIDATED|VALIDATED|REJECTED
PROMOTION_DECISION=TEST|RESERVE|PROMOTE|HOLD|REJECT
CANONICAL_KEYWORD_ID_IF_PROMOTED
WHY
```

`AI_DISCOVERY / WEB_DISCOVERY` 必须与真实观察数据隔离保存；候选词进入 Canonical Keyword Master 时必须保留 Provenance，不得把模型联想伪装成 ABA/SQP/PPC 等一方数据。

### 1A.6 TYPED / CONVERSATIONAL / SHOPPER QUESTION BANK
每 Child 同时维护：
- `TYPED_SEARCH_KEYWORDS`：核心词与长尾；
- `CONVERSATIONAL_QUERIES`：自然问句、场景、限制条件、比较表达；
- `SHOPPER_QUESTIONS`：尺寸、适配、材质、用途、安装、兼容、差异选择、痛点等。

目标是给 02/03/04/05 提供语义输入，不是假设 Alexa/Rufus 内部打分机制。

### 1A.7 TRANSPARENT PRIORITY SCORING｜可选透明评分
当数据足够且评分有决策价值时，可使用 0–100 或区间评分，但必须显示分项与证据，至少覆盖：
`Demand | Relevance | Purchase Proximity | Differentiation | Truth Support | Conversion Signal | Cross-channel Value | Risk Penalty`。

数据不足时使用 `HIGH/MEDIUM/LOW` 或分数区间；禁止为了看起来精确而伪造 87/100。

### 1A.8 SEARCH INTENT & BENEFIT PRIORITY CONTRACT
除 Keyword Master 外，必须形成可被 02/03/04/05 直接消费的：
```text
INTENT_ID
SEARCH_INTENT
REPRESENTATIVE_KEYWORDS
DEMAND_STRENGTH
PURCHASE_STAGE
CONSUMER_NEED
DESIRED_BENEFIT
PAIN_POINT_OR_OBJECTION
PRODUCT_TRUTH_SUPPORT
MESSAGE_PRIORITY
VARIATION_OWNER
LISTING_ROLE
VISUAL_ROLE
A_PLUS_ROLE
ADS_ROLE
EVIDENCE_SOURCE
```

这份 Contract 是 01 的核心专业交付之一，不允许退化成“关键词列表”。
