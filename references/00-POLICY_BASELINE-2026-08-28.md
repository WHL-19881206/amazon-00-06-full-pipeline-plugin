# Reference｜Amazon Policy Verified Baseline 2026-08-28

> 从原版 00 迁移的版本化 Baseline，仅作为 Runtime Refresh 失败时的受控回退证据。动态政策执行时应优先核查当前官方来源，不得让本文件覆盖更新后的平台事实。

### 7.3 CURRENT VERIFIED BASELINE｜2026-08-28
#### US-TITLE-2026-07-27
- Marketplace：Amazon US
- Scope：非媒体类目
- Title / Item Name：`≤75 characters including spaces`
- Item Highlights：`≤125 characters including spaces`
- Item Highlights：官方公告说明可搜索，并可出现在搜索结果与详情页
- Effective：2026-07-27
- Status：`ACTIVE`
- Supersedes：旧“多数类目 200 characters”默认基线
- Official source：News_Amazon, “Updates to improve your product titles begin on July 27”

任何适用项目在 Web 失败时仍使用此最近已验证基线，严禁回退到 200。

#### GENERAL-MAIN-IMAGE-BASELINE
当前 Amazon 官方卖家公开信息的高频基线：
- Main 准确代表实际售卖商品；
- 纯白背景 RGB 255/255/255；
- 商品应占画面约 85% 或以上；
- Main 不叠加文字、图形、水印；
- 不展示未包含且会误导的道具/配件；
- 官方公开卖家信息常见要求/建议最长边至少 1000 px 以支持 zoom；
- 类目特例、格式和其他尺寸限制运行时核查。

`JPG 2000×2000` 是用户生产标准，不是 Amazon 强制政策。

#### A+ DOCUMENTED CAPACITY BASELINE
当前 Amazon Seller Central 公开帮助对比页面可见：Basic A+ 详情页 allowable modules 为 5，Premium A+ 为 7；Brand Story 是独立的 A+ 内容类型/展示区，官方说明其可在 Basic 或 Premium A+ 之外使用。

本系统同时遵循用户长期标准：Basic/Premium 均按 7 个总模块规划，Brand Story 启用时计入 7 个。文档化数量视为 `DOCUMENTED_PLATFORM_LIMIT`，不是用来自动削减用户生产目标的 Hard Prohibition。

若最终实际平台只能装配更少：完整用户要求内容仍生产；可装配部分为 `ASSEMBLY_SET`，超出部分为 `RESERVE / ROTATION / FUTURE_ASSETS`；不得谎称一次已全部提交。
