# Shopify LLM Wiki

[项目本地 LLM Wiki](../.wiki/_index.md) 是项目主入口。此页保留操作文档导航。先找适用技能和已有结论，再开展工作。任务结束时保存结果，并将可复用且有依据的结论归入相应主题。技能正文保留一份，以下链接直接指向维护位置。

| 任务 | 技能和知识页 |
| --- | --- |
| 页面开发、体验验证、SimGym、上线和复盘 | [页面交付技能](../skills/shopify-page-delivery/SKILL.md) · [页面验证结论](topics/page-validation.md) |
| 后台操作、主题、API、渠道、支付和版本核查 | [Shopify 项目技能](../skills/shopify-project/SKILL.md) · [商家功能地图](../skills/shopify-project/references/merchant.md) · [开发地图](../skills/shopify-project/references/development.md) |
| 美国定制窗饰、样品复购、香港主体美元收款、Google 与 AI 购物 | [业务手册](../skills/shopify-project/references/window-coverings.md) |
| 政策、产品发布、套餐、API 版本变化 | [核查与更新方法](../skills/shopify-project/references/updates.md) |
| 近期执行与未决事项 | [执行记录目录](runs/index.md) · [记录模板](templates/run.md) |

## 读取和写回约定

1. 开始前按任务读取对应技能、主题页和最近相关执行记录，尤其检查尚未验证的结论。用户的新指令优先。产品状态、地区、版本、价格和权限有变化时，重新查官方来源。
2. 每项实质项目任务在 `.wiki/output/` 下创建 `YYYY-MM-DD-主题.md`，采用中国日期；同一任务的重试与复测更新原记录，用时间或版本标识多次结果。把记录加到 .wiki/output/_index.md，并追加 .wiki/log.md，并在记录中链接使用的技能。仅接收指令的消息无需单独建档。
3. 记录目标、执行范围、实际动作、可复现证据、结果、未决事项与下次条件。没有执行的测试写“待验证”，区分官方文档、模拟数据、示例测试和本店实测。链接项目内证据或访问受控的后台位置；只写必要的脱敏信息。
4. 新的长期结论写入对应主题页或已有手册，注明来源、日期、适用版本、店铺验证状态，并回链执行记录。出现冲突时保留历史记录，标明新结论取代哪条旧结论及原因。
5. 结束前检查新增链接可以打开，执行目录包含本次记录，知识页与执行证据一致。正式发布与收费操作按本次授权执行。
