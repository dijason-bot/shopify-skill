# 美国定制窗饰实操手册

已有业务背景为美国 DTC、香港公司 Shopify Payments、窗帘和窗饰硬件、样品到成品的邮件流程、Google 商品与广告。店铺套餐、支付结算配置、已发布主题和应用配置需要以最新后台为准。

## 1. 定制商品与订单

| 需要处理的内容 | 落地方式和验证点 |
| --- | --- |
| 可独立销售或计价的成品与硬件 | 按 SKU、售价、库存、渠道和售后需要决定商品及变体。对各尺寸/材质组合验证可售状态、价格、Feed 与履约映射 |
| 顾客在每个窗户上选的高度、宽度、安装方式和备注 | 评估主题表单、定制应用或自建配置器。用购物车行级属性沿商品页、购物车、订单、通知和工厂工单验收。两扇窗买同一 SKU 时要保留各自行配置 |
| 尺寸决定价格或加工规则 | 先写可复现价格表、尺寸区间、英寸分数、舍入及边界样例。核实变体、定制应用或合资格 Functions 的实现能力。结账、折扣、退款和导出逐个校验。顾客可编辑的行属性只能作为输入，成交价格以 Shopify 订单和服务端校验结果为准 |
| 测量说明与兼容关系 | 用 metafields 保存商品规格，用 metaobjects 维护共享内容，例如安装指南、轨道兼容性和布料护理。有关电机安全、证书和美国法规结论，绑定具体产品型号与实际证明文件，并查适用主管部门 |
| 出货与售后 | 在订单或履约系统保留工厂识别所需配置、交期、生产状态和修改窗口。验证部分履约、拆包、退款及历史订单的旧格式可读性 |

案例验收至少涵盖同 SKU 不同尺寸、边界尺寸、移动端、加速结账、折扣、售完与错误配置。检查客户看到的配置、后台行项目及加工单一致。 [商品](https://help.shopify.com/en/manual/products) · [自定义数据](https://help.shopify.com/en/manual/custom-data) · [Ajax Cart API](https://shopify.dev/docs/api/ajax/reference/cart) · [Functions](https://shopify.dev/docs/api/functions)

## 2. 香港主体、美国市场和美元订单

拿一笔有费用和一笔可比无费用的订单，记录时间、交易 ID、付款渠道、发卡地区、买家实付币种、店铺币种、支付账户国家或地区、实际结算币种和入账银行账户。用 Shopify Payments 交易与结算明细核对，向客户确认时只接收脱敏账单截图。

| 证据位置 | 要查什么 |
| --- | --- |
| Shopify 结账与订单明细 | 买家看见的商品价格、折扣、运费、税、关税，实际扣款币种和金额 |
| Shopify Payments 结算明细 | 每笔交易的处理、转换或结算费用、汇率、付款和入账币种，以及该笔费用由谁承担 |
| 发卡行账单 | 银行单列的境外交易费或汇兑收费。对照 Shopify 实扣金额和收款商户信息，向银行确认收费名称 |
| 市场与支付设置 | 美国市场币种、价格策略、结算账户支持、套餐及费率，再用代表性地址走一次结账 |

先归类再对客户回复。遇到“1.5%”这类数字，用费用标签、记录位置、币种与官方适用条款共同判定。 [香港 Shopify Payments](https://help.shopify.com/en/manual/payments/shopify-payments/supported-countries/hong-kong) · [跨境费用](https://help.shopify.com/en/manual/international/pricing/fees) · [Markets](https://help.shopify.com/en/manual/markets/)

## 3. 样品到成品

- 用明确的样品商品或 SKU 分类，并确定订单入口、售后状态及何时发出提醒。送达信号可用时验证承运商送达事件与覆盖率。使用发货时间作为代理时记录实际延迟口径。
- 在发送前重新检查营销许可、取消和退款、已购成品、历史触达。以客户 ID 和业务触发对象做去重，并跑一批测试客户。
- 跟踪样品订单数、符合条件人数、邮件送达以及 7/14/30 天成品购买率。按样品购买批次比较，只在相应观察窗口结束后计算成熟批次。需要估算增量时使用保留组。
- 面向美国客户的模板应说明样品与下一步，例如查看布料、选择样式或获取测量帮助。给客户一条明确的操作路径。

[Shopify Flow](https://help.shopify.com/en/manual/shopify-flow) · [营销](https://help.shopify.com/en/manual/promoting-marketing) · [客户](https://help.shopify.com/en/manual/customers)

## 4. Google Feed、归因与店铺转化

1. 在 Shopify 查商品/变体 ID、市场可售、Google & YouTube 发布和报错。再到 Merchant Center 抽查实际 ID、价格、库存、图片、运费、退货与目标落地页。对定制商品，用美国地址验证广告落地页、可购基础配置及审核数据一致。
2. 建立 SKU 或商品 ID 对照，区分样品、窗帘成品、电动产品与硬件。核对每类商品在 Feed、广告报表、Shopify 和工厂系统里的映射关系。
3. 用一个测试订单走完商品页、加车、结账和购买。核对浏览器、Shopify Customer Events、GA4 与 Google Ads 中购买事件、订单 ID、金额、币种及去重。按美国相应地区检查隐私配置和退出后的行为。
4. 拆分指标口径。Shopify 核对订单与净销售。Google Ads 以其账户时区、转化动作、转化价值及归因窗口评估。当订单从点击到付款有 1–4 周延迟时，按当时数据更新实际分布，诊断近期数据时保留已成熟区间。分别观察样品订单及后续成品订单。
5. 排查突然下滑时，先核对 Shopify 店铺链路、销售数据及支付/配送错误，再看广告消耗、受影响商品和追踪变更。保留稳定的时间、币种与市场口径进行同周期对比。

[Google & YouTube](https://help.shopify.com/en/manual/online-sales-channels/marketplaces/google) · [Shopify 分析](https://help.shopify.com/en/manual/reports-and-analytics) · [隐私设置](https://help.shopify.com/en/manual/privacy-and-security/privacy/customer-privacy-settings) · [Web Pixels](https://shopify.dev/docs/api/web-pixels-api)

## 5. Shopify Catalog 与 AI 购物

- 先在后台核对 Shopify Catalog 和各 AI 渠道的资格及发布状态。核对 Google AI Mode/Gemini 的商品来源与 Google & YouTube 或 Merchant Center 的连接。其他 AI 渠道按各自的目录、落地和结账路径验证。
- 首轮用有确定售价、库存和退货条件的窗帘杆或轨道检查商品可发现性。对按尺寸定价的成品，用实际买家路径验证配置、最终价格、交期和退货说明是否能正确显示。
- 记录目标渠道、可用地区、商品 ID、落地页或结账方式、费用、测试时间和订单来源。费用及资格随渠道而变，逐项查当前帮助页和后台。

[Shopify Catalog](https://help.shopify.com/en/manual/shopify-catalog) · [AI 渠道商品发现](https://help.shopify.com/en/manual/online-sales-channels/agentic-storefronts/products)

## 6. 店铺上线与回滚

- 定位目前生效的主题、应用、Flow、市场、支付或配送规则。在改动前保存相关设置、差异或主题副本。
- 采用最小测试范围，覆盖美国市场、手机、代表性地址、相关商品组合、实际订单数据及回退步骤。货币、合规、套餐和实际生效范围以后台与官方规则交叉验证。
- 上线后用一个可追踪订单或一次对账检查变化。记录时间、改动人、影响商品或市场、回退条件和验证结论。
