# Upwork 项目筛选助手

[English](README.md)

一个通过 Upwork 官方 MCP 搜索和评估软件开发职位的 Agent Skill。它根据使用者填写的技能、项目经历、报价和交付偏好筛选职位，输出本地 Markdown 报告。报告包含推荐理由、预计工时和收益、主要风险、Connects 成本，以及符合条件项目的 Proposal 草稿。

Skill 对 Upwork 只执行读取操作。投递、联系客户、消耗 Connects 和修改账号由使用者自行决定和操作。

[查看脱敏后的真实筛选报告](examples/sample-report.zh-CN.md)，了解推荐表、收益测算和双语 Proposal 草稿的实际样式。

## 快速开始

需要一个支持本地 Skill 和 MCP 的 Agent，以及你自己的 Upwork Freelancer 账号。将整个目录作为 Skill 使用，保留 `SKILL.md` 与 `config/`、`references/`、`state/` 的相对位置。可以在支持的客户端中调用 `$upwork-job-assistant`，也可以在当前项目中明确要求 Agent 使用 `SKILL.md`。

### 1. 连接 Upwork MCP

在使用 Skill 的 Agent 中添加官方 MCP 端点 `https://mcp.upwork.com/mcp`，并用你自己的 Upwork 账号授权。使用 Codex CLI 时，可以执行下面的命令添加连接并登录。

```bash
codex mcp add upwork --url https://mcp.upwork.com/mcp
codex mcp login upwork
```

认证由客户端与 MCP 管理。配置文件里只填写筛选所需的信息。

### 2. 填写本地档案与偏好

从 Skill 根目录复制中文模板，去掉文件名中的 `.example.zh-CN`，使用下面两个标准文件名。命令会保留已有配置。

```bash
[ -e config/profile.md ] || cp config/profile.example.zh-CN.md config/profile.md
[ -e config/preferences.yaml ] || cp config/preferences.example.zh-CN.yaml config/preferences.yaml
```

- 在 `config/profile.md` 填写真实能力、可引用的工作经历和项目案例、可用时间、沟通方式及披露限制。删去虚构填写示例。
- 在 `config/preferences.yaml` 按自己的技能修改搜索词、职位类型和筛选偏好。时薪、预算底线与费率等字段可留空，报告会标明缺少的估算依据。
- 中文模板会输出中文报告，并生成中文审阅稿和英文候选投递稿。已有配置可直接将 `output.language` 改为 `zh-CN`，并将 `output.proposal_languages` 设为 `[zh-CN, en]`。档案可以直接用中文填写。
- Skill 会按上述语言设置读取中文规范。需要让执行入口本身也显示中文时，可先备份 `SKILL.md`，再将 [SKILL.zh-CN.md](SKILL.zh-CN.md) 复制为 `SKILL.md`。

### 3. 开始筛选

向 Agent 发送这样的请求。

> 使用 Upwork Job Assistant，按本地能力档案和筛选偏好查找近期项目。生成 Markdown 报告，给出推荐、条件推荐和对应的 Proposal 草稿。

首次运行以空状态和配置的回溯期开始。成功生成报告后，Skill 会在 `state/` 记录运行时间和 Job ID，下次据此增量搜索并复查仍待决定的项目。也可手动初始化状态。已有状态会保留。

```bash
[ -e state/run-state.json ] || cp state/run-state.example.json state/run-state.json
[ -e state/job-history.json ] || cp state/job-history.example.json state/job-history.json
```

## 如何使用报告

报告区分当前适合投标的项目和有明确前置条件的项目。先看筛选理由、预计交付范围、投入和收益估算，再核对真实职位、申请成本和草稿内容。职位搜索覆盖受 MCP 的数据、排序和分页限制。评分用于比较项目，收益取决于实际费率、工时和范围。

可将「已投递」「跳过」「保留观察」等决定告诉 Agent，供后续筛选和去重使用。也可以根据多个实际结果调整搜索词和评分偏好。

## 文件一览

| 文件 | 用途 |
|---|---|
| [SKILL.zh-CN.md](SKILL.zh-CN.md) | 中文执行流程与 Upwork 只读边界 |
| [config/profile.example.zh-CN.md](config/profile.example.zh-CN.md) | 能力、经历和项目填写模板 |
| [config/preferences.example.zh-CN.yaml](config/preferences.example.zh-CN.yaml) | 搜索、评分和报告偏好模板 |
| [config/proposal-guide.zh-CN.md](config/proposal-guide.zh-CN.md) | 按真实经历撰写 Proposal 的规则 |
| [references/report-format.zh-CN.md](references/report-format.zh-CN.md) | 报告内容与字段规则 |
| [references/state-management.zh-CN.md](references/state-management.zh-CN.md) | 增量搜索和状态更新规则 |
| [state/](state/) | 可公开的空状态模板 |

## 本地数据与隐私

Git 默认忽略填写后的两份配置、`reports/` 下的运行报告和 `state/` 下的实际状态文件。若修改报告或状态输出目录，请同步更新 `.gitignore`。公开报告样例前，移除个人资料、原帖链接、账号凭证、投递记录及运行诊断标识。

本项目使用 [MIT License](LICENSE)。
