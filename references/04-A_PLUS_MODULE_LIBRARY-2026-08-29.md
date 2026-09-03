# Reference｜A+ Built-in Module Library

> 从 2026-08-29 原版 04 原样迁移。它是静态/候选模块知识库，不是每次执行都必须全部加载的 Runtime 指令。执行时先确定 Basic/Premium 与候选模块，再只读取相关模块定义；当前 Amazon UI/模块能力与本 Reference 冲突时，以当前官方/账户事实为准。

## 6A. BUILT-IN A+ MODULE LIBRARY｜基础 A+ + Premium A+ 全模块内置基线

> 本节是 04 的**内置模块知识库**，直接吸收用户提供的《基础A+》与《高级A+》PDF 中的全部模块定义；**不替代**上文 `DYNAMIC MODULE CATALOG` 与当前 Seller Central / Amazon Policy 核查机制。
>
> - Basic A+ 来源：`Basic A+ Module Guide｜基础 A+ 模块指南｜仅 PC 端`，Version 1.3，2026-08-29；模块顺序按 Seller Central “Add Module”，规格按官方 SP-API A+ Content Examples。
> - Premium A+ 来源：`Premium A+ Module Guide`，Version 1.0，Last updated 2023-05-30。
> - 运行原则：以下内容作为 `BUILT_IN_MODULE_BASELINE`。正式生产时仍必须读取当前目标账户/Marketplace 可用模块；如当前 UI、政策或字段约束与本内置基线冲突，以当前已验证平台事实为准，并记录 `MODULE_CATALOG_DEVIATION`，不得静默改写历史基线。
> - 用户长期生产标准仍保持：Basic/Premium 默认均规划 7 个总内容模块；本节的“模块库数量”不等于单次 A+ 必须使用的模块数量。

### 6A.1 EMBEDDED MODULE SCHEMA｜内置模块统一字段

每次做模块选择时，先从本节映射到统一结构：

```text
MODULE_TYPE_ID
MODULE_NAME
A_PLUS_TYPE=BASIC|PREMIUM
SOURCE_GUIDE
SOURCE_VERSION
RECOMMENDED_USE_CASE
IMAGE_OR_VIDEO_SPEC
MOBILE_LAYOUT
DESKTOP_LAYOUT
CHARACTER_LIMITS
FIELDS_OR_STRUCTURE
SOURCE_NOTES
CURRENT_AVAILABILITY
CURRENT_POLICY_STATUS
VERIFIED_DATE
```

其中 `CURRENT_AVAILABILITY / CURRENT_POLICY_STATUS / VERIFIED_DATE` 必须在运行时更新；PDF 未提供的字段不得推断为官方事实。

---

### 6A.2 BASIC A+｜17 个 Standard 模块完整内置

**SOURCE_SCOPE**：仅 PC 端。模块名称与顺序按 Seller Central 当前 “Add Module” 界面；最低图片尺寸、图片 Alt Text 上限与文本字段字符上限按该指南引用的 Amazon 官方 SP-API A+ Content Examples。

#### BASIC-01｜Standard Company Logo｜标准公司徽标
- `RECOMMENDED_USE_CASE`：Place a clean brand logo at the start or end of the A+ sequence. / Reinforce brand recognition without repeating product claims. / Keep the logo simple enough to remain legible at display size.
- `PC_LAYOUT`：Image minimum `600 × 180 px`。
- `CHARACTER_LIMITS`：Image alt text `≤100`；无 headline/body text 字段。
- `FIELDS_OR_SLOTS`：`1 required image`；Company logo + required image alt text。

#### BASIC-02｜Standard Comparison Chart｜标准比较图
- `RECOMMENDED_USE_CASE`：Compare products within the same brand/catalog. / Clarify size, material, feature, or use-case differences. / Support cross-sell and correct product selection.
- `PC_LAYOUT`：Optional product image，minimum `150 × 300 px`。
- `CHARACTER_LIMITS`：Metric name `≤100`；product title `≤80`；ASIN `≤10`；image alt text `≤100`；metric text `≤250`。
- `FIELDS_OR_SLOTS`：Up to `6 product columns`；Product title/ASIN、optional image、highlight flag、metric rows、metric values。

#### BASIC-03｜Standard Four Image & Text｜标准四图与文本
- `RECOMMENDED_USE_CASE`：Present four benefits, features, steps, or use cases in parallel. / Use when each point needs equal visual weight. / Keep all four images stylistically consistent.
- `PC_LAYOUT`：Each image minimum `220 × 200 px`，共 4 图。
- `CHARACTER_LIMITS`：Main headline `≤200`；each block headline `≤160`；each block body `≤1000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`4 required images`；Main headline + 4 image/headline/body blocks。

#### BASIC-04｜Standard Four Image/Text Quadrant｜标准四图/文本象限
- `RECOMMENDED_USE_CASE`：Explain four compact feature → benefit pairs. / Use when text needs more space than in a four-column strip. / Best for simple images or icons that remain clear at small size.
- `PC_LAYOUT`：Each image minimum `135 × 135 px`，共 4 图。
- `CHARACTER_LIMITS`：Each quadrant headline `≤160`；body `≤1000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`4 required images`；4 image/headline/body quadrants。

#### BASIC-05｜Standard Image & Dark Text Overlay｜标准图片 + 深色文字叠加
- `RECOMMENDED_USE_CASE`：Create a wide lifestyle or feature banner. / Use a bright/open image where a dark text box remains readable. / Reserve enough negative space for the overlay.
- `PC_LAYOUT`：Image minimum `970 × 300 px`。
- `CHARACTER_LIMITS`：Headline `≤70`；body `≤300`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required background image`；DARK overlay color + optional headline/body。

#### BASIC-06｜Standard Image & Light Text Overlay｜标准图片 + 浅色文字叠加
- `RECOMMENDED_USE_CASE`：Create a wide lifestyle or feature banner. / Use a darker image where a light text box has strong contrast. / Keep critical product details outside the overlay zone.
- `PC_LAYOUT`：Image minimum `970 × 300 px`。
- `CHARACTER_LIMITS`：Headline `≤70`；body `≤300`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required background image`；LIGHT overlay color + optional headline/body。

#### BASIC-07｜Standard Image Header With Text｜标准图片标题 + 文本
- `RECOMMENDED_USE_CASE`：Lead with a high-impact hero or lifestyle image. / Explain a primary value proposition with more visual depth than an overlay banner. / Use as a strong opening or section break.
- `PC_LAYOUT`：Image minimum `970 × 600 px`。
- `CHARACTER_LIMITS`：Headline `≤150`；subheadline `≤150`；body `≤6000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required image`；Headline + subheadline/body block + image。

#### BASIC-08｜Standard Multiple Image Module A｜标准多图片模块 A
- `RECOMMENDED_USE_CASE`：Show several angles, use cases, variants, or details without stacking multiple modules. / Let shoppers inspect related visual states in one content block. / Keep the sequence coherent rather than mixing unrelated imagery.
- `PC_LAYOUT`：Image minimum `300 × 300 px per block`。
- `CHARACTER_LIMITS`：Each block headline `≤160`；description `≤1000`；caption `≤200`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：Image/text blocks；each block contains image、optional headline、description、caption；thumbnail is generated from the highlight image。

#### BASIC-09｜Standard Product Description Text｜标准产品描述文本
- `RECOMMENDED_USE_CASE`：Add extended explanation, instructions, background, or contextual product information. / Use when the content does not require another visual asset. / Structure copy for scanning rather than creating a dense text wall.
- `PC_LAYOUT`：No image。
- `CHARACTER_LIMITS`：Body text `≤6000`；无 headline field。
- `FIELDS_OR_SLOTS`：`0 image slots`；Body-text-only module。

#### BASIC-10｜Standard Single Image & Highlights｜标准单图与亮点
- `RECOMMENDED_USE_CASE`：Summarize a major feature with supporting sub-points. / Pair one strong visual with compact structured benefits. / Use when bullets improve scanability.
- `PC_LAYOUT`：Image minimum `300 × 300 px`。
- `CHARACTER_LIMITS`：Headline description `≤160`；subheadlines `≤200`；body 1 `≤1000`；bodies 2–3 `≤400`；tech-spec headline `≤160`；bullet text `≤100`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required image`；Headline/description blocks + tech-spec headline + `1–8 bullet positions`。

#### BASIC-11｜Standard Single Image & Sidebar｜标准单图与侧边栏
- `RECOMMENDED_USE_CASE`：Combine a primary story with a secondary proof point or context block. / Separate “what it is” from “why it matters” inside one module. / Use the sidebar for complementary information, not repetition.
- `PC_LAYOUT`：Main image minimum `300 × 400 px`；sidebar image minimum `300 × 175 px`。
- `CHARACTER_LIMITS`：Main headline `≤160`；main subheadline `≤200`；main body `≤500`；main bullets `≤200`；caption `≤200`；sidebar headline `≤200`；sidebar body `≤500`；sidebar bullets `≤200`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`2 required images`；Main image/caption area + sidebar image/text area，含 headline/body/list fields。

#### BASIC-12｜Standard Single Image & Specs Detail｜标准单图与规格详情
- `RECOMMENDED_USE_CASE`：Explain detailed features, compatibility, setup, or product specifications. / Combine one product image with structured technical content. / Useful for reducing fit/specification uncertainty.
- `PC_LAYOUT`：Image minimum `300 × 300 px`。
- `CHARACTER_LIMITS`：Headline `≤200`；description headline `≤160`；description subheadline `≤200`；description body `≤400`；tech-spec headline `≤160`；tech-spec subheadline/bullets `≤200`；tech-spec body `≤1000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required image`；Description fields + specification fields，含 `1–8 bullet positions` 与 specification text block。

#### BASIC-13｜Standard Single Left Image｜标准左侧单图
- `RECOMMENDED_USE_CASE`：Build a simple feature → benefit narrative with image first. / Alternate with the right-image module to create visual rhythm. / Highlight a close-up, application, material, or result.
- `PC_LAYOUT`：Image minimum `300 × 300 px`。
- `CHARACTER_LIMITS`：Main headline `≤160`；main body `≤1000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required image`；`imagePositionType=LEFT` + headline/body block。

#### BASIC-14｜Standard Single Right Image｜标准右侧单图
- `RECOMMENDED_USE_CASE`：Continue an alternating left/right content sequence. / Give copy more prominence while retaining one supporting image. / Explain a second feature, use case, or objection.
- `PC_LAYOUT`：Image minimum `300 × 300 px`。
- `CHARACTER_LIMITS`：Main headline `≤160`；main body `≤1000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required image`；`imagePositionType=RIGHT` + headline/body block。

#### BASIC-15｜Standard Technical Specifications｜标准技术规格
- `RECOMMENDED_USE_CASE`：Present dimensional, material, electrical, compatibility, or component facts. / Reduce uncertainty for specification-driven purchases. / Use when exact facts matter more than persuasive imagery.
- `PC_LAYOUT`：No image。
- `CHARACTER_LIMITS`：Main headline `≤80`；spec name `≤30`；spec definition `≤500`；`4–16 specification rows`。
- `FIELDS_OR_SLOTS`：`0 image slots`；`4–16 specification rows`；`tableCount=1 or 2`。

#### BASIC-16｜Standard Text｜标准文本
- `RECOMMENDED_USE_CASE`：Add a concise transition, brand statement, instruction, or explanation. / Provide context that does not justify another image asset. / Use between visual modules when a short text bridge improves comprehension.
- `PC_LAYOUT`：No image。
- `CHARACTER_LIMITS`：Headline `≤160`；body text `≤5000`。
- `FIELDS_OR_SLOTS`：`0 image slots`；Optional headline + optional body text。

#### BASIC-17｜Standard Three Images & Text｜标准三图与文本
- `RECOMMENDED_USE_CASE`：Show three primary benefits, use cases, steps, or product details. / Create a balanced feature row with strong visual weight per item. / Use when three concepts form a clear, memorable set.
- `PC_LAYOUT`：Each image minimum `300 × 300 px`，共 3 图。
- `CHARACTER_LIMITS`：Main headline `≤200`；each block headline `≤160`；body `≤1000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`3 required images`；Main headline + 3 required image/headline/body blocks。

---

### 6A.3 PREMIUM A+｜Premium Module Guide 全模块完整内置

#### 6A.3.0 PREMIUM GLOBAL IMAGE REQUIREMENTS｜高级 A+ 全局图片要求
- `FILE_TYPE`：`.jpg | .bmp | .png`；animated GIF 不支持。
- `FILE_SIZE`：单张图片 `≤2MB`。
- `RESOLUTION`：至少 `72 dpi`。
- `COLOR_SPACE`：`RGB`；`CMYK` 不支持。
- Source note：图片大于模块最大尺寸时可被调整；小于模块限制时不会自动放大到满足最低要求；A+ Content Manager 可 crop/scale。
- Source note：指南建议使用 `Manage Your Experiments` 做 A/B test，以测试不同 A+ 版本对客户的效果。

#### PREMIUM-01｜Premium Full Image
- `RECOMMENDED_USE_CASE`：Close-up of product. / Customer using the product to show size/dimension or in a lifestyle setting. / Brand logo.
- `CHARACTER_LIMITS`：Headline `80`；Body `300`。
- `MOBILE_LAYOUT`：Image minimum `600 W × 450 H px`。
- `DESKTOP_LAYOUT`：Image minimum `1464 W × 600 H px`。

#### PREMIUM-02｜Premium Text
- `RECOMMENDED_USE_CASE`：Allows greater character limits than other modules for explaining more details or instructions on your product.
- Source guidance：Highlight unique features and benefits；use clear and concise language；content should be engaging and persuasive.
- `CHARACTER_LIMITS`：Headline `80`；Body `300`。
- `IMAGE_OR_VIDEO_SPEC`：PDF 未提供图片要求。

#### PREMIUM-03｜Premium Background Image with Text
- `RECOMMENDED_USE_CASE`：Close-up of product. / Customer using the product to show size/dimension or in a lifestyle setting. / Highlight key product features/benefits — product “elevator pitch”.
- `CHARACTER_LIMITS`：Subheadline `40`；Headline `60`；Body `300`。
- `TEXT_BOX_NOTE`：Text box 可放 left 或 right；text color 可为 black 或 white。
- `MOBILE_LAYOUT`：Image minimum `600 W × 450 H px`。
- `DESKTOP_LAYOUT`：Image minimum `1464 W × 600 H px`。

#### PREMIUM-04｜Premium Four Images & Text
- `RECOMMENDED_USE_CASE`：Photos of all angles of the product. / Show different uses of the product. / Show different features of the product.
- `CHARACTER_LIMITS`：Subheadline `80`；Headline `30`；Body `150`。
- `MOBILE_LAYOUT`：No separate mobile image；utilizes desktop image assets。
- `DESKTOP_LAYOUT`：Image minimum `300 W × 225 H px`。

#### PREMIUM-05｜Premium Dual Images with Text
- `RECOMMENDED_USE_CASE`：Photos of all angles of the product. / Show different uses of the product. / Show different features of the product.
- `CHARACTER_LIMITS`：Subheadline `50`；Headline `50`；Body `300`。
- `MOBILE_LAYOUT`：No separate mobile image；utilizes desktop image assets。
- `DESKTOP_LAYOUT`：Image minimum `650 W × 350 H px`。

#### PREMIUM-06｜Premium Single Image with Text
- `RECOMMENDED_USE_CASE`：Close-up of product. / Customer using the product to show size/dimension of product. / Highlight key product features/benefits — product “elevator pitch”.
- `CHARACTER_LIMITS`：Subheadline `40`；Headline `80`；Body `500`。
- `MOBILE_LAYOUT`：No separate mobile image；utilizes desktop image asset。
- `DESKTOP_LAYOUT`：Image minimum `800 W × 600 H px`。

#### PREMIUM-07｜Premium Full Video
- `RECOMMENDED_USE_CASE`：Show how the product moves and operates. / Show how your product is assembled. / Show different uses of your product in action.
- `CHARACTER_LIMITS`：Headline `80`；Body `300`。
- `MOBILE_LAYOUT`：No separate mobile video/image；utilizes desktop assets。
- `DESKTOP_LAYOUT`：
  - Video type `.mp4 only`；Flash unsupported。
  - Video resolution minimum `960 × 540`。
  - Video size maximum `200 MB`。
  - Video length maximum `180 sec`。
  - Video preview image minimum `1464 W × 600 H px`。
  - Preview image file types：`png | jpg | jpeg`。
- Source note：指南称 ideal video length 为 `10 seconds or less`，并说明其观察到平均客户可能在此后停止观看。

#### PREMIUM-08｜Premium Video with Text
- `RECOMMENDED_USE_CASE`：Show how the product moves and operates. / Show how your product is assembled. / Show different uses of your product in action. / Use text to provide additional context or reinforce key points of the video.
- `CHARACTER_LIMITS`：Subheadline `40`；Headline `80`；Body `500`；Video title `50`；Video description `200`。
- `MOBILE_LAYOUT`：No separate mobile video/image；utilizes desktop assets。
- `DESKTOP_LAYOUT`：
  - Video minimum `800 W × 600 H px`。
  - Video size maximum `200 MB`。
  - Video length maximum `180 sec`。
  - Video preview image minimum `800 W × 600 H px`。
- Source note：PDF 页面包含 Premium A+ + video 的销售/调研统计；这些统计属于该 2023 指南中的说明性数据，**不得自动转化为本产品 Claim**。

#### PREMIUM-09｜Premium Comparison Table 1
- `RECOMMENDED_USE_CASE`：Show feature or use case differences between products in your catalog. / Show spec differences between products in your catalog, such as size, color, material. / Upsell opportunity for other product variations.
- `CHARACTER_LIMITS`：Module headline `80`；Image headline `25`；Feature `30`；Tooltip `150`；Detail `30`。
- `MOBILE_LAYOUT`：No separate mobile image；utilizes desktop image assets。
- `DESKTOP_LAYOUT`：Image minimum `200 W × 225 H px`。
- `STRUCTURE_LIMITS`：Products `4 min – 7 max`；Features `5 min – 12 max`。

#### PREMIUM-10｜Premium Comparison Table 2
- `RECOMMENDED_USE_CASE`：Show feature or use case differences between products in your catalog. / Show spec differences between products in your catalog, such as size, color, material. / Upsell opportunity for other product variations.
- `CHARACTER_LIMITS`：Module headline `80`；Image headline `30`；Feature `30`；Body Text `80`。
- `MOBILE_LAYOUT`：No separate mobile image；utilizes desktop image assets。
- `DESKTOP_LAYOUT`：Image minimum `300 W × 225 H px`。
- `STRUCTURE_LIMITS`：Products `2 min – 3 max`；Features `2 min – 5 max`。

#### PREMIUM-11｜Premium Comparison Table 3
- `RECOMMENDED_USE_CASE`：Show feature or use case differences between products in your catalog. / Show spec differences between products in your catalog, such as size, color, material. / Upsell opportunity for other product variations.
- `CHARACTER_LIMITS`：Chart headline `25`；Image headline `25`；Feature `20`；Feature Text `20`。
- `MOBILE_LAYOUT`：Image minimum `600 W × 450 H px`；mobile image needed for each panel。
- `DESKTOP_LAYOUT`：Image minimum `488 W × 700 H px`。
- `STRUCTURE_LIMITS`：Comparison products `2 min – 4 max`；Features `3 min – 7 max`。

#### PREMIUM-12｜Premium Hotspots 1
- `RECOMMENDED_USE_CASE`：Simplify and structure feature/benefit callouts for complex, feature-heavy products. / Answer questions such as “What does this button do?” and “What does this material look and feel like?”
- `CHARACTER_LIMITS`：Hotspot headline `50`；Hotspot body text `200`。
- `MOBILE_LAYOUT`：Image minimum `600 W × 450 H px`；mobile image needed for each hotspot。
- `DESKTOP_LAYOUT`：Image minimum `1464 W × 600 H px`。
- `STRUCTURE_LIMITS`：Hotspots `2 min – 6 max`。

#### PREMIUM-13｜Premium Hotspots 2
- `RECOMMENDED_USE_CASE`：Simplify and structure feature/benefit callouts for complex, feature-heavy products. / Answer questions such as “What does this button do?” and “What does this material look and feel like?”
- `CHARACTER_LIMITS`：Module headline `80`；Body text `300`；Hotspot headline `50`。
- `MOBILE_LAYOUT`：Image minimum `600 W × 450 H px`；mobile image needed for each hotspot。
- `DESKTOP_LAYOUT`：PDF 标注 image minimum `1464 W × 600 H px`（原文位置写作 “Image (for video preview)”）。
- `STRUCTURE_LIMITS`：Hotspots `2 min – 6 max`。

#### PREMIUM-14｜Premium Navigation Carousel
- `RECOMMENDED_USE_CASE`：Show feature or use case differences between products in your catalog. / Upsell opportunity for other products that may be of better value. / Photos of all angles of the product. / Show different uses of the product.
- `CHARACTER_LIMITS`：Navigation text `25`；Subheadline `25`；Headline `25`；Body text `100`。
- `MOBILE_LAYOUT`：Image minimum `600 W × 450 H px`；image needed for each panel。
- `DESKTOP_LAYOUT`：Image minimum `1464 W × 600 H px`；image needed for each panel。
- `STRUCTURE_LIMITS`：Panels `2 min – 5 max`。

#### PREMIUM-15｜Premium Regimen Carousel
- `RECOMMENDED_USE_CASE`：Show feature or use case differences between products in your catalog. / Upsell opportunity for other products that may be of better value. / Photos of all angles of the product. / Show different uses of the product. / Highlight key steps in using the product.
- `CHARACTER_LIMITS`：Module headline `100`；Inset headline text `20`；Inset body text `100`；Navigation text `20`。
- `MOBILE_LAYOUT`：Image minimum `600 W × 450 H px`；image needed for each panel。
- `DESKTOP_LAYOUT`：Image minimum `1464 W × 600 H px`。
- `STRUCTURE_LIMITS`：Panels `2 min – 5 max`。

#### PREMIUM-16｜Premium Simple Image Carousel
- `RECOMMENDED_USE_CASE`：Close-up of product. / Customer using the product to show size/dimension of product. / Highlight key product features/benefits — product “elevator pitch”. / Show feature or use case differences between products in your catalog.
- `CHARACTER_LIMITS`：Headline text `50`；Body text `200`。
- `MOBILE_LAYOUT`：Image minimum `600 W × 450 H px`；image needed for each panel。
- `DESKTOP_LAYOUT`：Image minimum `1464 W × 600 H px`。
- `STRUCTURE_LIMITS`：Panels `2 min – 6 max`。

#### PREMIUM-17｜Premium Video Image Carousel
- `RECOMMENDED_USE_CASE`：Shorter clips of different aspects, e.g. one clip of product use followed by one clip of assembly. / Use text to guide users through what each clip is.
- `CHARACTER_LIMITS`：Headline `80`；Panel headline `50`；Panel subheadline `80`；Panel body text `500`；Video title `50`；Video description `200`。
- `MOBILE_LAYOUT`：No separate mobile video/image；utilizes desktop asset。
- `DESKTOP_LAYOUT`：
  - Video type `.mp4 only`；Flash unsupported。
  - Video resolution minimum `800 × 600`。
  - Video size maximum `200 MB`。
  - Video length maximum `180 sec`。
  - Image minimum `800 W × 600 H px`。
  - Image file types：`png | jpg | jpeg`。
- `STRUCTURE_LIMITS`：Panels `2 min – 6 max`。

#### PREMIUM-18｜Premium Q&A
- `RECOMMENDED_USE_CASE`：Proactively answer frequently asked questions. / Address common concerns that lead to customer complaints or returns.
- `CHARACTER_LIMITS`：Question text `120`；Answer text `250`。
- `MOBILE_LAYOUT`：No separate mobile image；utilizes desktop asset；Q&A `2 min – 5 max`。
- `DESKTOP_LAYOUT`：Image minimum `1464 W × 600 H px`；Q&A `2 min – 5 max`。
- Source tip：Customer feedback in reviews is a useful source for deciding what to address。

#### PREMIUM-19｜Premium Technical Specifications
- `RECOMMENDED_USE_CASE`：Simplify key product details so customers can make informed purchase decisions.
- `CHARACTER_LIMITS`：Headline `80`；Specification `30`；Definition `500`。
- `DESKTOP_AND_MOBILE_LAYOUT`：Same layout。
- `STRUCTURE_LIMITS`：Specifications `4 min – 16 max`。

---

### 6A.4 PREMIUM GUIDE REFERENCE PATTERN｜Brand Highlight / Get Started 示例逻辑内置

> 以下不是额外模块类型，而是《Premium A+ Module Guide》末尾展示的组合用法与模块职责示例。保留它们用于模块编排判断，但不得把示例品牌事实写入其他产品。

- `Premium Full Video` 示例职责：展示产品如何构造、成品近景，降低线上无法实物查看带来的购买障碍；另一个视频示例展示使用方法、不同材料上的 tips/tricks 与使用结果。
- `Premium Full Image` 示例职责：使用简单的产品近景 + 大字，简洁表达 feature 与 benefit；Lifestyle + tagline 可用于建立品牌联想。
- `Premium Navigation Carousel` 示例职责：用生活方式场景展示产品可使用的不同区域/场景。
- `Premium Q&A` 示例职责：回答材料适配、适用对象等高频问题，主动降低投诉/退货风险。
- `Premium Comparison Table` 示例职责：展示规格，并帮助买家在品牌内相似产品之间正确选择。
- `Brand Story` 示例职责：位于 “From the brand” / “From the manufacturer” 额外区域，用于品牌识别、品牌差异、品牌价值与品牌内其他商品展示；该指南示例还展示了高流量时期促销/畅销品曝光的用法。**实际运行必须继续受 04 的 Brand Truth、Claim Firewall 与当前 Amazon Policy 约束。**
- Visual pattern：示例强调有限的品牌色、简单不拥挤的图片、聚焦关键细节的文字。

### 6A.5 BUILT-IN MODULE SELECTION RULES｜内置后调用规则

1. **不得因为已内置 36 个模块定义而固定套模板。** 先做 `SHOPPER_TASK → QUESTION → MODULE_FIT`，再选模块。
2. Basic A+ 选型时优先从 `BASIC-01…BASIC-17` 读取；Premium A+ 选型时优先从 `PREMIUM-01…PREMIUM-19` 读取。
3. 当前账户无法使用某一模块时，保留原 `SHOPPER_TASK`，换成当前可用且信息损失最小的模块；记录 `MODULE_SUBSTITUTION_REASON`。
4. 图片生产尺寸仍执行 04 既有长期标准：`PRODUCTION_DIMENSIONS = CURRENT_VERIFIED_SLOT_MIN × 2`；本节 PDF 尺寸是最低尺寸基线，不直接替代运行时当前核查。
5. 字符上限以当前验证值为最终装配约束；如当前值与内置 PDF 不一致，保留 PDF 基线并写入 `MODULE_CATALOG_DEVIATION`。
6. Premium 2023 指南中的任何统计、示例品牌、示例产品、促销或“转化提升”描述均不得作为用户产品的事实/Claim 直接复用。
7. Basic 指南明确为 PC-only；若任务涉及 mobile，必须继续执行 04 的 `MOBILE COMPRESSION TEST` 并读取当前平台行为，不得从 Basic PDF 推断未提供的移动端规格。
8. 每个最终选定模块都必须在 `MODULE RECORD` 中写明其内置库编号，例如 `BUILT_IN_MODULE_ID=BASIC-07` 或 `PREMIUM-12`。
