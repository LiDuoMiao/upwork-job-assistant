# Upwork 项目筛选报告 · 脱敏样例

> 来源为一次实际筛选。保留了当时的统计、评分和收益估算。职位名称已概括，原帖链接和投递记录已移除，草稿中的个人经历已省略。职位情况和费率均按当时的报告口径展示。

## 运行摘要

本轮搜索约 130 条结果，去重后约 70 个项目，职位主要发表于最近两天。深入核验 8 个新项目，复查 5 个历史待决定项目。新增推荐投标 1 个，条件推荐 1 个。

## 推荐投标

| 得分 | 项目 | 客户地区 | 预算 | 预计投入 | 毛收入 / 扣平台费后 | 竞争 / Connects | 判断 |
|---:|---|---|---:|---|---|---|---|
| 79 | 支付记录与邮件收据自动化 | 美国 | 固定价 $250 | 7–10 小时 | $250 / $212.50–250 | Proposal 数未知；当时无面试、Offer 或雇佣；11 Connects | 单流程、验收明确，按预算折算约 $25–35.7/小时。收益估算可靠性中 |

## 条件推荐

| 得分 | 项目 | 客户地区 | 预算 | 预计投入 | 毛收入 / 扣平台费后 | 竞争 / Connects | 投递前需要确认或接受 |
|---:|---|---|---:|---|---|---|---|
| 75 | PDF 文档问答助手 | 澳大利亚（账号显示） | 固定价 $500 | 20–28 小时 | $500 / $425–500 | 50+ 份 Proposal，3 人进入面试；11 Connects | 确认可在 5 天内交付解析、引用、评测和部署。若资料需要大量 OCR，应缩小首版范围或重新估价。投递需花 11 Connects，客户可能不回复。收益估算可靠性低 |

收益按原报告使用的 0%–15% 平台费情景估算，未扣税费、汇兑及提现成本。可靠性根据预算、范围和工时信息的充分程度评定。

## 仍值得考虑的历史项目

当时复查的 5 个职位仍开放，原判断为 2 个推荐投标、3 个条件推荐。本节仅展示复查汇总。

## 单项目分析

### 支付记录与邮件收据自动化

**项目介绍**　客户需要一条可导入的 n8n 工作流。流程接收支付 Webhook、校验字段、写入 Airtable、生成并发送 HTML 收据，同时处理重复事件与基本失败情况。交付包括流程 JSON 和配置说明。

- **匹配与评分**　需要 API 集成和工作流自动化能力。投递前先核对是否能独立完成 n8n、Airtable 和邮件服务配置。技术 28/35、交付 17/20、预算 12/15、客户 10/15、竞争 8/10、需求清晰度 4/5，合计 79。
- **客户与进展**　客户为新账号，未显示雇佣记录。职位当时开放，尚无面试、Offer 或雇佣。Proposal 数和付款验证状态未核实。
- **报价与收益**　按发布预算 $250 报这条工作流，估计 7–10 小时，毛时薪约 $25–35.7，扣平台费后约 $212.50–250。新增支付网关对接、多收据模板或运维可另行估价。
- **是否值得消耗 Connects**　值得考虑。项目范围明确，11 Connects 对这份小合同的申请成本尚可。投递前可检查现有工具是否足以实现全部步骤。

#### 中文 Proposal 草稿

我会先确认 Webhook 里哪个字段能唯一标识一笔付款，再把记录和发邮件做成可独立检查的步骤。重复收到同一笔付款时，流程应能识别已处理的记录，避免发出第二封收据。交付前我会用正常、字段缺失和重复推送三类事件验证，并附上可导入的 n8n 流程和配置说明。

发送 Webhook 的支付系统是哪一个？你们是否已经有可用的邮件服务？按目前的一条工作流估算，固定报价为 $250。

#### English Proposal draft

I would first check which webhook field uniquely identifies a payment, then make the Airtable write and the email step independently verifiable. When the same payment arrives twice, the workflow should recognize the existing record and avoid sending a second receipt. Before handing over the importable n8n workflow and setup notes, I would test valid events, missing fields, and duplicate deliveries.

Which payment system sends the webhook, and do you already have an email service set up? My fixed quote for the single workflow described is $250.

### PDF 文档问答助手

**项目介绍**　客户希望把数十份产品资料、流程文档和 FAQ 做成内部问答助手。系统需要解析 PDF、检索相关段落、返回文件名和页码，并在证据不足时说明无法回答。首版要提供 API、简易聊天页、Docker 部署、评测摘要和演示，交付周期约 4–5 天。

- **匹配与评分**　工作涉及 PDF 解析、带引用的检索问答和应用部署。需要评估扫描件比例、逐页引用的可行性，以及是否能在短周期内完成全部交付。技术 33/35、交付 12/20、预算 8/15、客户 10/15、竞争 7/10、需求清晰度 5/5，合计 75。
- **客户与进展**　职位当时开放，已有 50+ 份 Proposal、3 人进入面试。客户账号未显示雇佣历史。
- **报价与收益**　固定预算 $500，估计 20–28 小时，毛时薪约 $17.9–25，扣平台费后约 $425–500。扫描件比例、部署环境和验收样题未知，估算可靠性低。
- **投递前需要确认或接受**　先确认 5 天内能交付的范围。若资料可直接提取、界面保持简洁，可按 $500 提议首版。若需要大量 OCR 或额外权限功能，需重新界定范围与工期。接受花 11 Connects 争取一次沟通机会，客户可能不回复。

#### 中文 Proposal 草稿

我会先抽几份代表性 PDF 检查文本和页码能否准确保留，然后用一组真实问题验证检索结果是否指向正确页面，再接入聊天页。还会加入文档里找不到答案的测试题，检查系统能否如实说明依据不足。

资料中扫描件占多少？能否提供几道典型问题和目标部署环境？如果多数文档可以直接提取、界面保持简洁，$500 可作为首版预算。大量 OCR 或复杂权限需要单独估算。

#### English Proposal draft

I would start with a representative set of PDFs to check that text and page numbers survive extraction. Then I would use real questions to verify that retrieval points to the right pages before connecting it to the chat UI. I would also test questions the documents cannot answer to see whether the assistant makes the lack of evidence clear.

How many documents are scanned, and can you share a few typical questions and the target deployment environment? If most documents can be extracted directly and the UI stays simple, $500 is a workable budget for the first version. Extensive OCR or complex permissions would need a separate estimate.

## 校准附录：未推荐项目

| 项目 | 暂不推荐原因 |
|---|---|
| 电商流程自动化 | 单一名额已完成雇佣，继续投递需花 27 Connects |
| AI SaaS 产品开发 | 职位主要涉及项目协调、轻量技术支持和客户沟通，具体开发任务不清楚 |
| 能源平台全栈开发 | 首版同时包含网站、订阅、电子协议、后台和 AI 报告，范围大且预算未公开 |

## 覆盖说明

部分搜索和详情查询发生连接中断，重试后恢复了一部分结果。普通搜索的分页有限，报告中的数量只代表本轮返回的样本。
