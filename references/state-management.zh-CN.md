# 增量搜索与历史状态管理

## 状态文件

从 Skill 根目录解析配置中的状态路径。默认使用 `state/run-state.json` 和 `state/job-history.json`。文件缺失时用 [空白运行状态](../state/run-state.example.json) 和 [空白项目历史](../state/job-history.example.json) 中的结构作为初值。保留已有的有效状态。若现有状态无法解析，说明问题并保留原文件。

运行状态保存 `last_successful_run_at`、`last_deep_backfill_at` 和 `last_config_version`。时间使用带时区的 ISO 8601 格式。

历史中的 `jobs` 以稳定 Job ID 为键。可记录标题、公开链接、发布时间、首次及最近发现时间、最新判断、用户决定、评估配置版本和相对报告路径。省略完整职位描述、客户反馈原文、个人账号标识、Connects 余额、Trace ID、Proposal 全文和认证信息。

## 时间窗口和分页

- 首次运行以 `first_run_lookback_days` 为起点。每轮固定 `run_started_at` 为搜索窗口终点。
- 常规运行从上次成功时间减去 `overlap_hours` 开始，用 `max_regular_lookback_days` 限制最大回溯。超出窗口的区间写入覆盖说明。
- 启用补漏后，在首次常规运行成功后的下一轮执行首次补漏。后续以 `last_deep_backfill_at` 和 `interval_days` 判断是否到期。补漏使用更长的 `lookback_days` 和独立的分页上限。用户也可以明确请求一次补漏。
- 对每条最新或按时间排序的路线，在无下一页、整页已经早于窗口或达到配置的分页上限时停止。对没有服务端时间筛选的路线，按返回的发布时间截取。到达上限时，说明可能尚有窗口内结果。

## 跨次筛选

`last_decision` 常用值如下。

| 状态 | 含义与后续处理 |
|---|---|
| `seen` | 搜索中出现但未进入详情分析。深度补漏、规则或职位的实质变化可触发重新评估 |
| `recommended` | 当前支持花费 Connects，在提醒期内可复查 |
| `conditional` | 需满足前置条件，在提醒期内可复查 |
| `watch` | 用户要求观察，在提醒期内可复查 |
| `not_recommended` | 当前不推荐，重要信息或相关规则变化时再评估 |
| `applied` | Upwork 已显示投递，或用户确认已投，排除出推荐 |
| `dismissed` | 用户明确跳过，排除出推荐 |
| `closed` | 职位关闭、无法申请或招聘完成，保留历史 |

按配置限制历史复查范围和数量。职位的预算、描述、招聘进展或用户决定变化时，才补做相关分析。明确反馈记录在 `user_disposition`，详情中的 `applied=true` 也足以排除推荐。

## 保存顺序

先保存 Markdown 报告，再保存更新后的历史，最后将 `last_successful_run_at` 更新为 `run_started_at`，并记录当次配置版本。成功完成补漏时，同时更新 `last_deep_backfill_at`。任一关键步骤失败时，保留原成功时间，下次继续覆盖该区间。历史以 Job ID 合并，重试时复用已有记录。
