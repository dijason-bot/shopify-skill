---
title: "页面校验的实测边界 · 迁移底稿"
type: notes
tags: [project-baseline]
summary: "项目文档的原始快照，保留完整内容及基线提交。"
source: "wiki/topics/page-validation.md"
ingested: 2026-11-18
sha256: 732a1dc82eb6f45d4aca00507a530c8303cccd34214cadf6a8a73e71c3afc79a
---

# 页面校验的实测边界 · 来源快照

基线提交 a4e269a，原路径 wiki/topics/page-validation.md。

~~~~markdown
# 页面验证结论

| 核查日期 | 可复用结论 | 证据与范围 |
| --- | --- | --- |
| 2026-11-18 | 本项目可以启动 Shopify Dev MCP 1.13.3。在同一会话中先调用 `learn_shopify_api` 选择 `liquid`，取得 conversationId，再用 `validate_theme` 验证变更文件。持续修改同一文件时沿用 artifactId 并递增 revision | 已在临时主题示例执行失败及成功路径。完整 Codex 插件安装受本机缓存权限限制。[执行记录](../runs/2026-11-18-page-validation.md) · [官方 Toolkit](https://shopify.dev/docs/api/ai-toolkit) |
| 2026-11-18 | 本项目将 SimGym 用于上线前发现购物摩擦。主题对比的第二个主题须为草稿。选取建议后看回放，确认触达目标页面，再复现和复测 | 官方文档核对，店铺资格、余额和模拟报告待店铺实测。[SimGym](https://help.shopify.com/en/manual/online-store/simgym) |
| 2026-11-18 | 实际购买、订单行属性、计价、退款及上线后业务指标分别验证。窗饰用例覆盖同 SKU 的两组尺寸、样品与成品、移动端和加速结账 | 项目验收设计，后续按订单或脱敏测试记录更新。[页面交付技能](../../skills/shopify-page-delivery/SKILL.md) · [窗饰手册](../../skills/shopify-project/references/window-coverings.md) |

项目内 MCP 启动入口为 `tools/shopify-dev-mcp`（stdio）。本机保留已验证的离线运行依赖，归档中的启动器在其他机器缺少依赖时按官方 npm 包启动，需要网络和兼容 Node.js。其他机器如已安装 Shopify AI Toolkit，可以直接从插件调用相应能力。
~~~~
