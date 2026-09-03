# Reference｜Skill 06 Professional Capability Modules

> 从业务深度保留版主 Runtime 迁移。此文件不是“被删除内容”；当主 Skill 的 LOAD WHEN TRIGGERED 条件成立时必须读取并执行。ALWAYS ACTIVE 要点已在主 Runtime 摘要保留。

## 1A. PROFESSIONAL CAPABILITY ENHANCEMENT｜模板编译与发布 QA 专业增强

### 1A.1 WORKBOOK ROLE DETECTION｜文件角色先于文件名
每个工作簿先判定：
`CATEGORY_REPORT | UPLOAD_TEMPLATE | LISTING_FINAL | IMAGE_MANIFEST | PROCESSING_REPORT | REFERENCE_ONLY | UNKNOWN`。

判定依据：Sheet、Field ID、Header、Data Definitions、Valid Values、样例结构、已有 SKU/ASIN，不得仅凭文件名。

### 1A.2 MARKETPLACE / PRODUCT-TYPE TEMPLATE ISOLATION
禁止：
- 把 US Template 用于 DE/JP/UK 等其他站点；
- 把 A Product Type 的 Field ID/Valid Value 套到 B Product Type；
- 把旧模板的 Variation Theme 当当前模板真值；
- 仅因为列名相似就跨模板映射。

每个最终文件必须绑定：`MARKETPLACE | CATEGORY | PRODUCT_TYPE | TEMPLATE_VERSION | TEMPLATE_SOURCE | RELEASE_ID`。

### 1A.3 PRE-WRITE SCHEMA DIFF
写入前生成：
```text
SOURCE_TEMPLATE_HASH_OR_ID
SHEET_LIST
HEADER_SIGNATURE
FIELD_ID_SIGNATURE
DATA_VALIDATION_SIGNATURE_IF_READABLE
FORMULA/MACRO_PRESENCE
EXPECTED_WRITE_COLUMNS
UNEXPECTED_SCHEMA_CHANGE
```

若与当前 Release 预期模板不一致，先更新 Mapping Registry，不用旧映射盲写。

### 1A.3A MAPPING PROFILE｜可复用映射规则资产
06 必须把可安全复用的 Mapping 从单次执行记录提升为受模板版本约束的 Profile：

```text
MAPPING_PROFILE_ID
MARKETPLACE
CATEGORY
PRODUCT_TYPE
TEMPLATE_VERSION
TEMPLATE_SOURCE
HEADER_SIGNATURE
FIELD_ID_SIGNATURE
DATA_VALIDATION_SIGNATURE_IF_READABLE
MAPPING_REGISTRY_VERSION
LAST_VALIDATED_DATE
REUSE_ELIGIBILITY
INVALIDATION_REASON
```

只有 Marketplace/Product Type/Template Schema 兼容时才允许复用；任何 Header/Field ID/Valid Value/Variation Theme 关键变化都必须使旧 Profile 失效并重新解析，不能为了“复用”盲写。

### 1A.4 SAFE VERSIONING / ROLLBACK PACKAGE
默认不覆盖用户原始模板。保留：
- `ORIGINAL_SOURCE`；
- `WORKING_COPY`；
- `FINAL_UPLOAD_COPY`；
- `WRITE_AUDIT`；
- `RELEASE_MANIFEST`。

如果用户明确要求覆盖，也必须先保留可回滚副本或记录原值。这样 Processing Report 出错时可以定位某一版本，而不是失去原始基准。

### 1A.5 BATCH RECONCILIATION
批量 SKU 必须守恒：
```text
INPUT_SKUS
EXPECTED_OUTPUT_ROWS
WRITTEN_ROWS
BLOCKED_ROWS
SKIPPED_NOT_APPLICABLE
DUPLICATES
UNMATCHED_SKUS
```

`EXPECTED_OUTPUT_ROWS = WRITTEN_ROWS + BLOCKED_ROWS + SKIPPED_NOT_APPLICABLE`（按当前操作定义调整）。任何 SKU 静默消失均 FAIL。

### 1A.6 LOCALIZATION / VALUE FORMAT VALIDATION
06 不翻译营销文案，但必须验证目标模板要求的：
- decimal/date/number formatting；
- measurement units / unit fields；
- marketplace-valid enum；
- local language required fields；
- currency/price field context（任务包含时）；
- warning/label/compliance field presence（模板要求时）。

如果转换会改变业务语义或事实，回流 Source Owner，不自行“格式化成看起来能过”。

### 1A.7 UPDATE SEMANTICS MATRIX
对每个写入字段明确：
`CREATE_VALUE | UPDATE_VALUE | KEEP_EXISTING | CLEAR_VALUE | NOT_APPLICABLE | BLOCKED`。

Blank ≠ Clear；0 ≠ Blank；父体空值 ≠ Child 值；旧值存在 ≠ 一定覆盖。必须结合 Operation Type、Template instruction 与 Source Ownership。

### 1A.8 ERROR ROOT-CAUSE KNOWLEDGE BASE
Processing Report / Validation Error 至少归类：
`SOURCE_MISSING | FIELD_MAPPING | INVALID_ENUM | REQUIRED_CONDITION | DATA_TYPE | CHARACTER_BYTE | VARIATION | SKU_RELATION | POLICY | IMAGE_URL | RELEASE_MISMATCH | AMAZON_SYSTEM_OR_UNKNOWN`。

同类错误应沉淀到当前项目 Mapping Registry / validation rule，避免修复一个 SKU 后其余 SKU 重复报错。
