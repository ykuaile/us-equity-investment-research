# 美股长期投资研究助手

[English](README.md)

`us-equity-investment-research` 是一个本地指令型 Skill，用于一次研究一只美股。它输出一张带日期和来源的研究卡，分别说明公司质量、估值条件、下行风险和持仓披露线索。

本项目仅用于教育与研究，不构成投资、法律、税务或会计建议，也不建立投资顾问关系。它不提供短线信号、仓位比例或买入、卖出、交易指令。详见 [DISCLAIMER.md](DISCLAIMER.md)。

## 研究卡回答的问题

1. 这家公司是否值得进入研究名单？
2. 什么估值条件适合分批考虑，而不是给出虚假精确的买入价？
3. 当前最大的下行风险是什么，它是否与估值安全边际匹配？
4. 论点依赖哪些假设，后续哪些事件会要求重估？

13F 只是长期机构关注的历史线索。它不能决定买点，也不能还原机构成本。

## 本地安装

把本目录复制到 `$CODEX_HOME/skills/us-equity-investment-research`；未设置 `CODEX_HOME` 时复制到 `~/.codex/skills/us-equity-investment-research`。如果新 Skill 没有出现，刷新或重启 Codex。可使用 `$us-equity-investment-research` 显式调用。

此包只有操作说明，不包含抓取器、数据库、API key、个人观察列表、付费行情缓存或 CUSIP 映射库。

## 数据边界

- EDGAR 原始文件是 13F 持仓事实的唯一主来源。
- 每条 13F 结论都必须展示报告期、提交日、文件类型、自然日滞后和原始链接。
- 缺失的价格、预期或文件必须保持缺失，不能编造。
- Apache-2.0 许可本项目的代码和文档，不许可行情、交易所数据或 CUSIP 数据库。

## 目录

```text
us-equity-investment-research/
├── README.md
├── README.zh-CN.md
├── DISCLAIMER.md
├── LICENSE
├── .gitignore
├── SKILL.md
├── agents/openai.yaml
└── references/
    ├── research-framework.md
    └── data-boundaries.md
```

## 许可证

[Apache License 2.0](LICENSE)
