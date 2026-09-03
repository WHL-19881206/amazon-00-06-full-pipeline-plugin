# Amazon 00–06 Full Pipeline Plugin

一个统一入口、七个独立内部 Skill 的 Amazon 生产插件包。

## 结构

- `SKILL.md`：插件统一入口与 Router，只负责路由/串联，不替代 00–06。
- `skills/amazon-00` … `skills/amazon-06`：七个独立 Skill，每个目录有自己的 `SKILL.md`。
- `references/`：按需加载的专业 Reference。
- `original-reference/`：旧版完整定义，仅用于深度追溯/审计，不参与默认 Runtime。
- `tests/`：测试资产。
- `docs/`：自检、优化与能力保持说明。

## 两种主要使用方式

### 自动路由
直接描述任务，例如：
- “帮我研究这个新品的关键词和搜索意图。”
- “根据这些资料做 Listing。”
- “把商品分类报告和上传模板映射好，生成最终 Excel。”

插件入口根据 Owner 责任选择最小必要 Skill/链路。

### 显式调用
- `AMAZON 00`
- `AMAZON 01`
- `AMAZON 02`
- `AMAZON 03`
- `AMAZON 04`
- `AMAZON 05`
- `AMAZON 06`
- `AMAZON FULL_PIPELINE_NEW_PRODUCT`

自然语言“调用 03”“用 05 做 PPC”等同样有效。

## 关键设计

- 一个插件，不等于一个巨型 Skill。
- 七个 Skill 保持 Owner Boundary 与独立专业能力。
- Router 只加载必要 Skill，防止 00–06 全量上下文同时激活。
- Full Pipeline 才按 00→01→02→03→04→05→06→00 Final QA 执行。
- Standalone 不降业务深度，也不强迫无关上游先跑。
