# Amazon 00–06 Full Pipeline Plugin

一个统一入口、七个独立内部 Skill 的 Amazon 生产插件。

## Production Repository Structure

- `SKILL.md`：插件统一入口与 Router，只负责路由/串联，不替代 00–06。
- `plugin.manifest.json`：插件与内部 Skill 路由清单。
- `ENTRY_COMMANDS.md`：显式调用入口。
- `skills/amazon-00` … `skills/amazon-06`：七个独立 Skill；每个目录包含自己的 `SKILL.md` 与 `skill.json`。
- `references/`：按需加载的专业 Reference；当前共 9 个。
- `docs/ROUTING_ACCEPTANCE.md`：Router 验收案例。

> 历史 `original-reference/` 与 Mock 二进制测试工作簿不属于生产 Runtime，因此不放入正式插件主仓库，避免 ChatGPT/Codex 误加载旧规则或测试资产。历史版本与完整本地测试包单独归档。

## 自动路由

直接描述任务，例如：
- “帮我研究这个新品的关键词和搜索意图。” → `01`
- “根据这些资料做 Listing。” → `02`
- “做 9 张 Listing 图片。” → `03`
- “把商品分类报告和上传模板映射好，生成最终 Excel。” → `06`

插件入口根据最终业务结果、Owner Boundary 与真实依赖选择最小必要 Skill/链路，不机械加载全部 00–06。

## 显式调用

- `AMAZON AUTO`
- `AMAZON 00`
- `AMAZON 01`
- `AMAZON 02`
- `AMAZON 03`
- `AMAZON 04`
- `AMAZON 05`
- `AMAZON 06`
- `AMAZON FULL_PIPELINE_NEW_PRODUCT`

自然语言“调用 03”“用 05 做 PPC”“运行 06”等同样有效。

## Full Pipeline

`00_INIT → 01 → 02 → 03 → 04 → 05 → 06 → 00_FINAL_QA → RELEASE_DECISION`

Full Pipeline 是 dependency-aware，不是一个局部失败就冻结全部链路。真正 Required Final Assets 仍必须在 Final Release 前完成。

## 核心设计原则

- 一个插件，不等于一个巨型 Skill。
- 七个 Skill 保持 Owner Boundary 与独立专业能力。
- 00 仍是 Product Truth / Policy / Governance / Orchestration / Final QA Owner；Root Router 不替代 00。
- Router 只加载必要 Skill 与必要 Reference，减少无关上下文。
- Standalone 不降低业务深度，也不强迫无关上游先跑。
- Business Output First，但 Product Truth、Variation、Policy、真实 Final Asset 与 Hard QA 不降级。
- 局部失败 → 局部返工；已合格资产保留。
