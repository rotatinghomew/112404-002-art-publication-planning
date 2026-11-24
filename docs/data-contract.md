# 合成资料约定

资料用于本地业务流程演练，字段仅记录事实来源，不预先裁定业务结果。

- `editions.csv`：拟发行的出版物版次，资料不预设印量。字段为 `edition_id, language, format, planned_release, article_set, image_set, price`。
- `permissions.csv`：图文许可按内容、媒介、地区和期间记录。字段为 `content_id, rightsholder, medium, territory, valid_from, valid_to, adaptation_allowed, state`。
- `orders.csv`：预售和渠道承诺，客户与渠道均使用合成代号。字段为 `order_id, edition_id, channel, ordered_at, quantity, state, change_consent`。
- `production.csv`：印制供应商的起订量、交期与批次。字段为 `printer_id, format, minimum_qty, lead_days, unit_cost, batch_id, received_qty`。
- `sales_returns.csv`：销售、退货和退款按发生时间记录。字段为 `event_id, edition_id, channel, event_date, event_type, quantity, maturity_date`。

空字段表示事实尚未提供，`pending`、`review`、`hold` 等状态表示来源记录尚未形成最终确认。不同来源以事件日期或有效期表达的时间含义不相同，调用方应结合表名和字段解释；不能仅因编号相同就假定两条记录可合并。金额以资料中记载的名义单位表示，没有统一换算或预先扣除退款。
