---
name: amazon-00-06-full-pipeline
description: "Amazon 00–06 full-pipeline plugin for ChatGPT/Codex. Routes Amazon seller tasks to seven independent internal skills: 00 governance/policy/orchestration, 01 search demand & keywords, 02 listing copy, 03 listing images, 04 A+ content, 05 Ads/PPC, 06 native upload template compiler. Supports automatic routing, explicit skill invocation, multi-skill chains, and FULL_PIPELINE_NEW_PRODUCT."
metadata:
  plugin_type: orchestrated_skill_suite
  version: "2026-09-03"
  internal_skills: 7
---

# Amazon 00–06 Full Pipeline Plugin

## 1. PURPOSE

This file is the **plugin entry/router**, not a replacement for Skill 00–06.
The plugin contains seven independent internal Skills under `skills/amazon-00/` through `skills/amazon-06/`.

Highest rule: **route first, then load only the selected Skill(s)**. Do not preload all seven Skill bodies unless the user explicitly requests the full pipeline or the task genuinely spans the full chain.

## 2. INTERNAL SKILLS

| Skill | Owner responsibility | Primary business output |
|---|---|---|
| `00` | Amazon policy, Product Truth, Variation/Claim governance, orchestration, final release QA | Policy/Truth constraints, routing, release decision |
| `01` | Search demand, keywords, intent, buyer needs, selling-point and downstream priority | Search/Keyword Decision Package |
| `02` | Amazon Listing copy | Title, Highlights, Bullets, Description, Search Terms |
| `03` | Amazon Listing image production | Main + PT01–PT08 final image set / production assets |
| `04` | Amazon A+ content production | Final A+ module architecture, copy and visual assets |
| `05` | Amazon Ads/PPC build and optimization | Executable PPC build/optimization assets |
| `06` | Amazon native upload template compilation | Final Amazon native upload workbook + validation |

Canonical files:
- `skills/amazon-00/SKILL.md`
- `skills/amazon-01/SKILL.md`
- `skills/amazon-02/SKILL.md`
- `skills/amazon-03/SKILL.md`
- `skills/amazon-04/SKILL.md`
- `skills/amazon-05/SKILL.md`
- `skills/amazon-06/SKILL.md`

## 3. INVOCATION MODES

### A. AUTO_ROUTE
Default when the user gives an Amazon business task without naming a Skill.
Determine the **minimum owner set** needed to complete the requested business output, then load and execute only those Skill files.

Examples:
- “研究这个新品的关键词、搜索意图和九图优先级” → `01`
- “根据这些关键词写 Listing” → `02`
- “做 9 张 Listing 图片” → `03`
- “做 A+” → `04`
- “给这个新品做 PPC” → `05`
- “把商品分类报告映射到上传模板并填好 Listing” → `06`
- “核查 Amazon 当前规则/变体/Product Truth” → `00`
- “关键词研究后直接写 Listing” → `01 → 02`
- “从原始产品资料完成 Listing + 九图 + A+” → choose the minimum valid chain, normally `01 → 02 → 03 → 04`, with `00` only where governance/policy/truth orchestration is actually required.

### B. EXPLICIT_SKILL
If the user explicitly names `00`, `01`, `02`, `03`, `04`, `05`, or `06`, route to that Skill directly.
Accepted examples:
- `调用 01`
- `Amazon 02`
- `用 03 做九图`
- `运行 06`
- `@amazon 05`

Explicit invocation has priority over AUTO_ROUTE unless it would violate a hard truth/policy/tool boundary. A selected Skill may perform its own Standalone Intake; do not force unrelated upstream Skills to run merely because they exist.

### C. FULL_PIPELINE_NEW_PRODUCT
Trigger when the user explicitly asks for the full 00–06 pipeline, complete new-product production, or explicitly invokes `FULL_PIPELINE_NEW_PRODUCT`.
Fixed owner sequence:
`00_INIT → 01 → 02 → 03 → 04 → 05 → 06 → 00_FINAL_QA → RELEASE_DECISION`

The full pipeline is **dependency-aware**, not a global stop-the-world transaction. A local non-dependent rework item does not freeze unrelated downstream production. Final release still requires all true required final assets and hard checks.

### D. MULTI_SKILL_CHAIN
For a task spanning several owners but not all seven, select the smallest valid ordered chain. Do not add Skills whose outputs are irrelevant to the user's requested result.

## 4. ROUTING PRIORITY

Use this order:
1. User explicitly named Skill / Full Pipeline mode.
2. Requested final business output.
3. Owner boundary of 00–06.
4. Hard dependency requirements.
5. Reuse of already valid upstream assets.
6. Minimum additional work.

Do not route based merely on keyword overlap. Route by **owner responsibility and requested deliverable**.

## 5. LOAD POLICY

After routing:
1. Read the selected `skills/amazon-XX/SKILL.md` in full enough to execute its current task.
2. Load only the Reference sections that the selected Skill explicitly requires or whose trigger condition is met.
3. Reuse valid current-release assets instead of rerunning unrelated Skills.
4. Do not load `original-reference/` during normal production. It is historical/deep audit material only.
5. Do not load `tests/` unless validating the plugin/Skill or running a test scenario.

### Reference map
- 00 → `references/00-GOVERNANCE_PROFESSIONAL_MODULES.md`, `references/00-POLICY_BASELINE-2026-08-28.md`
- 01 → `references/01-SEARCH_INTELLIGENCE_PROFESSIONAL_MODULES.md`
- 02 → `references/02-LISTING_PROFESSIONAL_MODULES.md`
- 03 → `references/03-VISUAL_PRODUCTION_PROFESSIONAL_MODULES.md`
- 04 → `references/04-A_PLUS_PROFESSIONAL_MODULES.md`, `references/04-A_PLUS_MODULE_LIBRARY-2026-08-29.md`
- 05 → `references/05-PPC_PROFESSIONAL_MODULES.md`
- 06 → `references/06-TEMPLATE_COMPILER_PROFESSIONAL_MODULES.md`

## 6. ORCHESTRATION RULES

- Each internal Skill remains an independent Owner. The router must not rewrite or absorb its business responsibility.
- Skill 00 is both an independent governance Skill and the full-pipeline orchestration/final-QA Owner. The root router only chooses and opens Skills; it does not replace 00 governance.
- Standalone execution must preserve the selected Skill's full professional depth. “Standalone” means fewer irrelevant dependencies, not lower quality.
- Use current verified Amazon Marketplace/Category rules when required. Do not substitute stale static memory for a dynamic hard rule.
- Product Truth, Variation/Child Truth, Claim evidence, and hard policy boundaries are never weakened for speed.
- Use tools for deterministic work and actual asset generation whenever available.
- Primary business output is delivered before optional diagnostics.
- Local failure → local rework. Preserve qualified outputs.
- Never claim an image, workbook, upload, campaign change, A+ submission, or other final/platform action exists unless it actually exists or was actually performed.

## 7. USER-VISIBLE ROUTING

Normally do not print a large routing report. If useful, one concise line is enough:
`ROUTE: 01 → 02` or `ROUTE: 06`.
Then execute the business task.

When the user explicitly asks which Skill was selected, report the selected Skill ID(s) and owner reason.

## 8. EXPLICIT ENTRY COMMANDS

The following semantic entry commands are supported:

```text
AMAZON AUTO
AMAZON 00
AMAZON 01
AMAZON 02
AMAZON 03
AMAZON 04
AMAZON 05
AMAZON 06
AMAZON FULL_PIPELINE_NEW_PRODUCT
```

Natural-language equivalents are valid; exact command syntax is not required.

## 9. PLUGIN COMPLETION

A plugin-level task is complete when:
- the requested Primary Business Output(s) from the selected Skill(s) are actually delivered;
- selected Skill Hard QA requirements are satisfied or precisely constrained;
- unresolved blockers are localized to their true owner/minimum unit;
- Full Pipeline requests additionally complete `00_FINAL_QA → RELEASE_DECISION`.

Do not treat router metadata, logs, or internal diagnostics as substitutes for business completion.
