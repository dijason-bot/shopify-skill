---
title: "Shopify 开发与 API · 迁移底稿"
type: notes
tags: [project-baseline]
summary: "项目文档的原始快照，保留完整内容及基线提交。"
source: "skills/shopify-project/references/development.md"
ingested: 2026-11-18
sha256: a78d81d816a62e5ccea3d354f136d1ba296fe7e21ef5ece1b644c2cbc81458ab
---

# Shopify 开发与 API · 来源快照

基线提交 a4e269a，原路径 skills/shopify-project/references/development.md。

~~~~markdown
# Shopify 开发与 API 地图

## 官方技能与验证工具

Shopify 当前推荐 **Shopify AI Toolkit**。该插件包含官方开发工作流，并按官方方式更新。官方文档提供统一的 `shopify` 技能，覆盖 Admin GraphQL、Functions、Polaris、Liquid、Hydrogen 和 Shopify CLI。原先的 `shopify-admin`、`shopify-liquid` 等分项技能已弃用。官方 commerce agent 文档另外列出 `ucp` 工作流。 [AI Toolkit](https://shopify.dev/docs/api/ai-toolkit) · [官方源码](https://github.com/Shopify/shopify-ai-toolkit) · [UCP 开发入口](https://shopify.dev/docs/agents)

| 需求 | 官方接入 |
| --- | --- |
| Codex 插件 | `codex plugin add shopify@openai-curated` |
| 按项目安装官方技能 | 在项目根目录运行 `npx skills add Shopify/shopify-ai-toolkit`，选择 Codex 和项目范围。官方文档使用 `npx skills update` 更新直接安装的技能 |
| Dev MCP | Shopify 的开发 MCP 提供文档、schema 与代码验证。配置和启动方式见 [AI Toolkit](https://shopify.dev/docs/api/ai-toolkit)。店铺数据访问需要独立的应用授权 |

## 开发面与落地入口

| 开发面 | 用途与验收关键点 | 官方入口 |
| --- | --- | --- |
| Admin GraphQL | 管理商品、订单、客户、库存、履约、Markets 和定义。固定受支持版本、核对权限，查询按游标分页，检查 GraphQL errors、mutation userErrors 和查询成本 | [Admin GraphQL](https://shopify.dev/docs/api/admin-graphql) · [限流](https://shopify.dev/docs/api/usage/limits) |
| 大批量数据 | 商品导出、批处理和持续同步。先确认该资源支持的批量操作，记录任务 ID、状态、失败记录和重跑边界 | [批量操作](https://shopify.dev/docs/api/usage/bulk-operations) |
| Storefront API | 买家端查询商品、集合、价格、购物车并取得结账链接。验证市场上下文、访问 token 类型、价格和可售状态 | [Storefront API](https://shopify.dev/docs/api/storefront) |
| Customer Account API | 面向买家的账户数据及授权。分别检查登录流程、客户或公司地点权限、订单可见性、账户扩展支持 | [Customer Account API](https://shopify.dev/docs/api/customer) |
| 主题与 Liquid | sections、blocks、JSON templates、snippets、settings schema、动态数据和 app blocks。运行 `shopify theme check`，用开发主题或预览测桌面、移动端和购物车 | [Themes](https://shopify.dev/docs/storefronts/themes) · [Liquid](https://shopify.dev/docs/api/liquid) · [CLI](https://shopify.dev/docs/api/shopify-cli) |
| Ajax、客户隐私和店面事件 | Liquid 店面购物车、预测搜索、买家隐私状态和店面交互。价格或披露变更要验证地域、本地化路径和实际结账行为 | [Ajax API](https://shopify.dev/docs/api/ajax) · [Customer Privacy API](https://shopify.dev/docs/api/customer-privacy) · [标准店面事件](https://shopify.dev/changelog/posts/standard-storefront-events-and-actions) |
| 自开发应用 | Dev Dashboard、CLI、框架模板、分发、安装和认证。创建前确认是店铺内用还是分发给外部商家，再按安装范围和授权选型 | [应用开发](https://shopify.dev/docs/apps/build) · [认证授权](https://shopify.dev/docs/apps/build/authentication-authorization) |
| 扩展与 Polaris | 用 App Home 或 Admin UI extensions 补后台；用主题 app extension 提供 app block/embed；分别检查 target、组件、能力和发布方式 | [应用扩展](https://shopify.dev/docs/apps/build/app-extensions) · [在线商店集成](https://shopify.dev/docs/apps/build/online-store) |
| Checkout、Customer Accounts、POS | 各自使用对应 UI Extension 及 target。上线前核对当前套餐、页面、API 版本、市场、可测试路径 | [Checkout UI](https://shopify.dev/docs/api/checkout-ui-extensions) · [Customer Account UI](https://shopify.dev/docs/api/customer-account-ui-extensions) · [POS UI](https://shopify.dev/docs/api/pos-ui-extensions) |
| Shopify Functions | 实施折扣、配送或支付定制、购物车验证及购物车变换等服务器端规则。先确认套餐、分发和具体 Function API 的约束，测试退款、叠加优惠和边界值 | [Functions](https://shopify.dev/docs/api/functions) |
| Webhooks 与事件 | 验证来源与签名，进行幂等处理并为重复、乱序或下游失败准备补偿。事件用于驱动同步，定期以 Shopify 权威数据对账 | [Webhooks](https://shopify.dev/docs/apps/build/webhooks) |
| Web Pixels | 使用标准客户事件和适用的沙箱/隐私能力。对比事件 ID、金额、币种和去重结果，分开检查 Ads、GA4 和 Shopify | [Web Pixels](https://shopify.dev/docs/api/web-pixels-api) |
| Hydrogen、Oxygen、headless | 自建店面渲染、边缘部署和 Storefront API 集成。验收 SEO、缓存、地区化、账户、结账、像素、主题应用的替代方案 | [Headless](https://shopify.dev/docs/storefronts/headless) · [Hydrogen](https://shopify.dev/docs/api/hydrogen) |
| ShopifyQL、分析与扩展能力 | 判断所需数据能否通过报表或 Admin GraphQL 取得，核对 ShopifyQL 支持、权限与数据范围。复杂指标保留原始订单和逻辑说明 | [ShopifyQL](https://shopify.dev/docs/api/shopifyql) · [开发 API 目录](https://shopify.dev/docs/api) |
| 公共应用与合作伙伴 | 应用审核、定价、计费、合规 Webhooks、保护客户数据、Partner/Dev Dashboard 管理 | [分发应用](https://shopify.dev/docs/apps/launch/distribution) · [受保护客户数据](https://shopify.dev/docs/apps/launch/protected-customer-data) |
| AI Commerce 与 UCP | 区分商家的 AI 销售渠道和面向买家构建的 commerce agent。开发时按实际商家 schema 校验发现、购物车、结账交接和订单追踪 | [Commerce agents](https://shopify.dev/docs/agents) |
| 平台其他入口 | 维护遗留 REST 集成时核对弃用；按需求查 Payment Apps、Shop Minis、Flow 扩展、主题商店和其他 API 的发布资格 | [API 全目录](https://shopify.dev/docs/api) · [开发更新](https://shopify.dev/changelog) |

## 技术选型与验收

1. 需要改商品展示或配置交互时，检查现有 Liquid 主题、动态数据、app block 和 Ajax Cart。需要店铺管理、跨系统同步时，查 Admin GraphQL 或应用扩展。需要独立买家店面时，查 Storefront API、Hydrogen 和账户集成。
2. 把重要校验放在覆盖相关入口的服务端设施中，并核对套餐与扩展能力。主题交互负责提示、可用性和采集，完整验收从商品页走到最终订单。
3. 把 API 版本、权限、运行账号、测试对象及回滚方式记入实现。出错时保留请求 ID、API 版本、查询成本、错误字段、处理结果和测试环境信息。使用脱敏数据。
~~~~
