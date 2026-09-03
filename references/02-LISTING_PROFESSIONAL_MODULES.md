# Reference｜Skill 02 Professional Capability Modules

> 从业务深度保留版主 Runtime 迁移。此文件不是“被删除内容”；当主 Skill 的 LOAD WHEN TRIGGERED 条件成立时必须读取并执行。ALWAYS ACTIVE 要点已在主 Runtime 摘要保留。

## 1A. PROFESSIONAL CAPABILITY ENHANCEMENT｜Listing SEO 与转化文案专业增强

### 1A.1 LISTING FIELD BUDGET COMPILER
在真正写文案前，先为每个 Child 建立字段预算，不先写完再硬塞关键词：
```text
FIELD
CURRENT_POLICY_LIMIT
MANDATORY_PRODUCT_IDENTITY
MANDATORY_VARIATION_INFO
KW_T1_MUST
KW_T2_PRIORITY
DIFFERENTIATOR
PROOF_OR_LIMITATION
OPTIONAL_TERMS
RESERVED_CHAR_OR_BYTE_BUDGET
```

Title/Item Highlights 空间紧时，优先保留：`产品身份 → 核心 Search Demand → 决定点击的真实属性/差异 → 必要 Variation 信息`。弱相关、低购买意图、已被更高效词根覆盖的内容优先下沉，而不是删除核心需求。

### 1A.2 LISTING CONTENT AUDIT｜Create / Optimize 的专业诊断
Optimize 模式至少独立审计：
- Product Truth errors；
- Search Demand coverage；
- Title front-load / mobile comprehension；
- Item Highlights role；
- Bullet decision-path completeness；
- Description semantic completeness；
- Backend byte efficiency；
- Variation isolation；
- Claim risk；
- Customer-language mismatch；
- CTR gap / CVR gap / Recommendation semantic gap。

Images/A+/Price/Reviews 可以作为诊断背景，但最终修改分别路由 03/04/运营，不越权。

### 1A.3 BACKEND SEARCH TERM ENGINE
Backend 不以“填满字节”为目标，而以**每一字节的新增搜索价值**为目标。执行：
1. 读取当前站点/类目/模板实际限制并做真实 byte count；
2. 从前台覆盖、同义词/词根、长尾、拼写变体、地区表达中计算 `MARGINAL_COVERAGE_VALUE`；
3. 删除无关、错误事实、错误 Child、侵权/受限内容与纯低价值重复；
4. 任何 dedupe 都必须保证不会误删唯一有效词根/语义；
5. “Title 已有所以 Backend 一律删除”不是全球固定真理，只有确认当前 indexing/space 逻辑后才使用；
6. 最终输出 `BYTE_USED / BYTE_LIMIT / INCLUDED_TERMS / EXCLUDED_TERMS / WHY`。

第三方 Skill 中的固定 250-byte、固定去重或“正好填到 249–250”只能作为历史/工具线索，不得覆盖当前官方/模板规则。

### 1A.4 CUSTOMER LANGUAGE → COPY
从 Review/Q&A/真实 Search Query 提取的消费者原生表达可用于提高本土化与理解速度，但必须区分：
- `CUSTOMER_LANGUAGE`：消费者如何描述需求；
- `PRODUCT_FACT`：产品真实具备什么；
- `CLAIM`：我们是否有证据可以主动宣称。

消费者说“很耐用”不等于可以无证据写“indestructible”；消费者常问某兼容型号也不等于产品兼容。

### 1A.5 FEATURE → BENEFIT → PROOF → USE CASE
核心文案尽量完成以下闭环，而不是只有 Feature：
```text
FEATURE / ATTRIBUTE
→ WHAT IT DOES
→ SHOPPER BENEFIT
→ PROOF / SPEC / LIMITATION
→ RELEVANT USE CASE
```

没有可验证 Proof 时，不能制造性能数字；可以使用真实结构/材质/尺寸/包装内含等事实降低购买不确定性。

### 1A.6 INDEXING / SEARCH VISIBILITY DIAGNOSTICS
如果用户提供 indexing、ranking、SQP/ABA/PPC 等结果，02 应判断：
- 词是否在 Listing 有正确语义承接；
- 是否因为字段缺失/错误属性/错误 Child 造成 relevance gap；
- 是否出现“已覆盖但曝光低”而问题更可能在竞争、广告、类目/索引或销量信号；
- 是否出现“曝光高但 CTR/CVR 弱”需要重写 Title/卖点或回流 03/04。

不得把“词出现了”直接等同“必然 indexed/rank 提升”。

### 1A.7 A/B HYPOTHESIS BACKLOG
对于可测试的 Title 前部、核心差异化表达、Bullet 顺序等，输出：
`HYPOTHESIS | VARIABLE | CONTROL | TEST_VERSION | PRIMARY_METRIC | GUARDRAIL | DECISION_RULE`。

只有真实实验数据才能宣称 lift；AI 不得预言“必提高 X%”。
