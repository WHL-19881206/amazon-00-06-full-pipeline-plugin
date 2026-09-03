# Reference｜Skill 05 Professional Capability Modules

> 从业务深度保留版主 Runtime 迁移。此文件不是“被删除内容”；当主 Skill 的 LOAD WHEN TRIGGERED 条件成立时必须读取并执行。ALWAYS ACTIVE 要点已在主 Runtime 摘要保留。

## 1A. PROFESSIONAL CAPABILITY ENHANCEMENT｜PPC 业务专业增强

### 1A.1 PROFITABILITY FRAMEWORK｜先定义经济边界
当真实数据可得时计算：
```text
NET_SELLING_PRICE
- PRODUCT/LANDED_COST
- AMAZON_FEES
- FULFILLMENT/SHIPPING
- PROMOTION/COUPON_COST
- RETURN/REFUND_ALLOWANCE (if known)
- OTHER_VARIABLE_COST
= CONTRIBUTION_BEFORE_ADS

BREAK_EVEN_ACOS = CONTRIBUTION_BEFORE_ADS / NET_SELLING_PRICE
TARGET_ACOS = 由目标利润、生命周期和战略目标反推
MAX_CPC_GUARDRAIL ≈ NET_SELLING_PRICE × TARGET_ACOS × EXPECTED_CVR
```

任何变量缺失都标记 Assumption/Range。`Target ACoS = Break-even ACoS - desired profit %` 只有在利润率口径一致时才可使用，不能机械套公式。

### 1A.2 CONTROLLED DISCOVERY FUNNEL｜可选而非教条
常见可控路径：
`Auto / Broad / Phrase discovery → Search Term validation → Exact/controlled owner → Scale/Maintain`。

但不是所有账号都必须固定 4 Campaign。根据预算、关键词数量、产品生命周期、Child 数、Brand/Ad type eligibility 选择结构。预算过小或数据不足时宁可减少结构，也不制造“结构很完整但每个 Campaign 没数据”的碎片化。

### 1A.3 SEARCH TERM DECISION CLASSIFICATION
每个 Search Term/Target 至少分类：
- `IRRELEVANT`；
- `RELEVANT_NO_SIGNAL_YET`；
- `RELEVANT_EXPENSIVE`；
- `PROFITABLE`；
- `STRATEGIC_GROWTH`；
- `HARVEST_CANDIDATE`；
- `NEGATIVE_CANDIDATE`；
- `LISTING_MISMATCH`；
- `WRONG_CHILD / WRONG_INTENT`。

动作必须基于分类，而不是只看 ACoS 红绿灯。

### 1A.4 EVIDENCE-SUFFICIENT THRESHOLD ENGINE
不得采用“2单就 Harvest”“10 clicks 0 sales 就 Negative”作为全账号硬规则。判断样本充分性至少考虑：
`CPC | Spend | ASP | Expected CVR | Actual CVR | Orders | Contribution Margin | Search Intent | Product Fit | Lifecycle | Data Window`。

可以给 `REVIEW_TRIGGER`，但必须说明为什么这个阈值在当前经济模型下合理。

### 1A.5 NEGATIVE TARGETING PROFESSIONAL RULES
Negative 的第一目的不是“清掉高 ACoS”，而是：错误意图过滤、错误 Child 防漏、Query Ownership、预算保护。

当前 Amazon Ads 官方帮助可见 Sponsored Products Negative Keyword 的常见 Console 匹配类型为 `negative phrase / negative exact`；Bulk Template/不同广告类型若出现其他 valid values，以**当前官方/模板实际枚举**为准，不用历史记忆猜。

当前 Amazon Ads 指南还建议：在把关键词设为 Negative 前，通常先观察到至少约 `20 clicks` 再评估表现。**这只能作为 `OFFICIAL_RECOMMENDATION / EVIDENCE SUFFICIENCY REFERENCE`，不是本系统的固定否词门槛。** 如果 Search Term 明确不相关、错误 Child、违反 Product Truth 或存在其他确定性错误意图，可以更早隔离；如果是战略核心词、样本噪声大或经济模型显示仍未达到充分样本，则即使超过 20 clicks 也不能机械否词。

Negative decision 必须记录：
```text
SEARCH_TERM_OR_TARGET
RELEVANCE
PERFORMANCE_EVIDENCE
NEGATIVE_SCOPE
NEGATIVE_TYPE
OWNER_AFTER_ACTION
EXPECTED_SAVING_OR_CONTROL
RISK_OF_OVER_NEGATION
ROLLBACK_CONDITION
```

### 1A.6 BID / BUDGET / PLACEMENT CONTROL LOOP
优化顺序：
1. Relevance/Intent 是否正确；
2. Listing 是否承接；
3. 经济上限；
4. Base bid；
5. bidding strategy；
6. placement adjustment；
7. budget availability；
8. observation window。

当前 Amazon Ads 能力中可能存在 dynamic down only / up and down / fixed / rule-based / audience bid / schedule rules 等；**只启用当前 Marketplace/Account 可确认能力**。

#### 1A.6.1 NO-NUMERIC-INPUT EXECUTION｜无数值不停机
用户未提供预算、CPC、CVR、利润或其他精确数值时，05 仍必须完成可执行的广告方案，不得因缺少数值终止，也不得伪造精确值。

- `BID`：优先表达为当前 Amazon 建议竞价、建议竞价区间、建议最低值，或其上下浮动的相对档位；未读取到当前账户建议值时，只输出计算逻辑与相对档位，不写伪精确金额。
- `BUDGET`：优先用“能够支持约 N 次有效点击的学习容量”设计测试预算，再以当前建议竞价/CPC 换算为账户币种金额；无实时 CPC 时保留公式或区间。
- `N`：只是学习容量、观察窗口或 `REVIEW_TRIGGER`，可依据相关性、意图、ASP、Expected CVR、CPC、利润、生命周期设为如 20/30 次点击等容量；不得把 20/30 或任何 X clicks 变成机械否词、Harvest、停投或扩量门槛。
- 相关性明确错误、Wrong Child、Product Truth 不支持或硬合规冲突时，可在未达学习容量前隔离；核心战略词即使达到观察值，也必须结合 CVR、经济边界与 Listing 承接再决策。
- 所有此类方案必须标记 `VALUE_BASIS=AMAZON_SUGGESTED|RELATIVE_RANGE|CLICK_LEARNING_CAPACITY|USER_CONFIRMED`，便于后续用真实账户数值替换。

### 1A.7 INVENTORY / PROMOTION / RETAIL READINESS
重大预算放大前检查：
`IN_STOCK | BUY_BOX/OFFER_ELIGIBILITY_IF_RELEVANT | DELIVERY_PROMISE | PRICE/PROMOTION | LISTING_VERSION | REVIEW_RATING_CONTEXT | VARIATION_AVAILABILITY`。

广告不能把流量送到缺货、错误 Child、低承接或价格/配送明显异常的页面后再怪 PPC。

### 1A.8 PERFORMANCE MEASUREMENT LAYERS
区分：
- `TRAFFIC`: impressions, CTR, CPC；
- `CONVERSION`: orders, CVR, CPA；
- `EFFICIENCY`: ACoS, ROAS；
- `BUSINESS`: TACoS, contribution after ads, total sales（数据可得时）；
- `GROWTH`: query rank/organic share/new-to-brand/impression share 等（账户数据可得时）；
- `LEARNING`: 新 Search Term、new ASIN target、audience insight。

不能只凭一个 ACoS 判断 Campaign 好坏。

### 1A.9 CONFIDENCE LABELS｜恢复专业判断分层
每项重大动作标记：
`FACT | DERIVED | STRATEGY | INFERENCE | UNVERIFIED`。

- FACT：报表/用户数据直接事实；
- DERIVED：明确公式计算；
- STRATEGY：基于数据的专业决策；
- INFERENCE：合理但未验证推断；
- UNVERIFIED：缺关键证据。

### 1A.10 PRE/POST ACTION AUDIT
每次结构性优化前后保留：
`Before State → Action Batch → Expected Mechanism → Observation Window → After State → Decision`。

避免同一时间改 Bid、Budget、Placement、Negatives、Listing 后无法判断哪个动作有效。


### 1A.11 AD TESTING PLAN / PPC EXPERIMENT BACKLOG｜广告测试策略
任何需要验证结构、匹配、Bid、Placement、Creative、Targeting 或 Budget 分配的实验，必须形成正式测试资产，而不是把“试一试”混入普通优化动作：

```text
TEST_ID
HYPOTHESIS
VARIABLE
CONTROL
TEST_VARIANT
CAMPAIGN_OR_TARGET_SCOPE
PRIMARY_METRIC
GUARDRAIL_METRIC
MINIMUM_EVIDENCE_RULE
TEST_WINDOW
DECISION_RULE
ROLLBACK_RULE
```

同一测试尽量控制关键变量；若必须批量改动，必须在 Pre/Post Audit 中标记 Confounding Risk。只有真实实验数据才能宣称 Lift。

### 1A.12 ORGANIC GROWTH ATTRIBUTION GUARDRAIL｜自然增长归因护栏
广告可以支持搜索词验证、销量与 Organic Growth，但不得把自然排名/Organic Share 变化机械归因于 PPC。涉及 `RANKING_GROWTH` 时至少记录：
`PAID_TRAFFIC_CHANGE | ORGANIC_RANK_OR_SHARE_CHANGE | TOTAL_SALES_CHANGE | LISTING_CHANGE | PRICE_PROMOTION_CHANGE | INVENTORY_CHANGE | COMPETITIVE_CHANGE | ATTRIBUTION_CONFIDENCE`。

无足够控制条件时只能表述为“与广告投入/订单变化同时发生、可能支持”，不得宣称“广告导致自然排名提升 X”。
