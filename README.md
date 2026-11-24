# 艺术出版物的分版印制与渠道备货分析

本项目保存视觉艺术机构日常业务分析使用的合成演练资料，样例不代表真实机构、作品、交易或研究结论。

## 资料

- `editions.csv`：拟发行的出版物版次，资料不预设印量。字段为 `edition_id, language, format, planned_release, article_set, image_set, price`。
- `permissions.csv`：图文许可按内容、媒介、地区和期间记录。字段为 `content_id, rightsholder, medium, territory, valid_from, valid_to, adaptation_allowed, state`。
- `orders.csv`：预售和渠道承诺，客户与渠道均使用合成代号。字段为 `order_id, edition_id, channel, ordered_at, quantity, state, change_consent`。
- `production.csv`：印制供应商的起订量、交期与批次。字段为 `printer_id, format, minimum_qty, lead_days, unit_cost, batch_id, received_qty`。
- `sales_returns.csv`：销售、退货和退款按发生时间记录。字段为 `event_id, edition_id, channel, event_date, event_type, quantity, maturity_date`。

记录之间通过 `*_id`、`*_key` 或 `*_ref` 字段关联。日期采用 ISO 格式；空值表示来源未提供该事实，不代表数值为零。不同来源的统计范围和状态以 `docs/data-contract.md` 为准。样例中保留了待确认、取消、缺失和版本变化等原始情况，不包含预先计算的分析结论。

## 运行

需要 Python 3.11 或更高版本，无第三方依赖。运行 `python3 -m unittest discover -s tests -v` 可检查资料编码、字段和记录结构。
