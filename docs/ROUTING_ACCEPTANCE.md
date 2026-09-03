# Routing Acceptance Cases

These cases validate router intent, not Amazon business correctness.

| Request | Expected route |
|---|---|
| 核查当前 Amazon 规则、Product Truth、Variation | `00` |
| 分析关键词、搜索意图、买家需求、九图优先级 | `01` |
| 写 Title/Bullets/Description/Search Terms | `02` |
| 生成 Listing 1+8 九图 | `03` |
| 生成 Amazon A+ | `04` |
| 做新品 PPC / 优化广告 | `05` |
| 商品分类报告映射上传模板并生成 Excel | `06` |
| 关键词研究后写 Listing | `01 → 02` |
| Listing 文案 + 9 图 | `02 → 03`（已有关键词/策略足够时）；否则按缺口补 `01` |
| 完整新品 00–06 全链路 | `00_INIT → 01 → 02 → 03 → 04 → 05 → 06 → 00_FINAL_QA` |
| 调用 04 | `04`，显式调用优先 |
| AMAZON 06 | `06`，显式调用优先 |

## Must-not-route cases

- 只写 Listing 不得机械强制跑 00→01→02；02 Standalone Intake 足够时直接 02。
- 只做 PPC 不得因为完整插件存在而加载 03/04/06。
- 只做模板映射不得让 04/05 成为默认依赖。
- Root Router 不得取代 00 的 Product Truth/Policy/Release QA 职责。
