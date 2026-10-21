---
name: us-equity-investment-research
description: Research one US-listed stock for long-term study. Use for company quality, valuation ranges, downside risk, thesis-breakers, and 13F, 13D/13G, or Form 4 context. Do not use for short-term trades, options strategies, position sizing, or buy and sell instructions.
metadata:
  short-description: Research one US stock long term
---

# US Equity Investment Research

Build a dated, source-backed research card for one US-listed ticker. The card answers whether the company deserves deeper study, which valuation conditions would create a margin of safety, what downside matters most, and which assumptions later events could break.

This is educational research, not investment, legal, tax, or accounting advice. It does not know the user's finances or risk tolerance. Never give a position size, a precise buy or sell price, or an instruction to buy, sell, or trade.

## Read before deciding

- For valuation, risk, monitoring, and filing-clue judgment, read [references/research-framework.md](references/research-framework.md).
- For EDGAR access, 13F interpretation, market data, missing data, and CUSIP boundaries, read [references/data-boundaries.md](references/data-boundaries.md).

Read only the reference relevant to the current question. Re-check an official source when a rule, deadline, or filing format may have changed.

## Scope

Accept one US-listed common stock, ADR, ETF, or closed-end fund and state which kind it is. Study the operating company behind an ADR when that is the economic exposure.

Do not turn one request into a market screen, portfolio, backtest, alert, or automated monitor. Do not place, prepare, or automate a trade. Do not save API keys, personal watchlists, trading records, paid-data caches, or a reusable CUSIP mapping database.

## Evidence order

Keep these layers separate. Do not merge them into one score or one sentence:

1. Business and financial quality.
2. Valuation and the assumptions behind each scenario.
3. Downside risk and observable thesis-breakers.
4. Filing clues from 13F, 13D/13G, and Form 4.

Finish the first three layers before using filing clues. A holding change cannot rescue weak quality, an unattractive valuation, or an unidentified risk.

## Evidence standard

- Label every material claim as fact, estimate, or inference.
- Attach a source URL and as-of date to every claim that can change.
- Say precisely what is missing. Never invent a price, consensus estimate, financial figure, filing, or date.
- Prefer primary filings and the issuer's reports over secondary summaries.
- Preserve reported values and state the unit. Flag suspicious values instead of silently correcting them.
- Treat a stale or undated figure as missing unless its age is disclosed and it is still fit for the question.

## Workflow

1. Identify the issuer, security, listing, reporting currency, and latest relevant filing. Note the price date separately from filing dates.
2. Assess the business, demand drivers, advantage or weakness, earnings quality, cash flow, capital allocation, and balance sheet.
3. Select a valuation method appropriate to the business. Build conservative, base, and optimistic scenarios, including the operating assumptions and why the conservative case could still be wrong.
4. Describe business, financial, valuation, and external risks, with an observable signal and a specific condition that would weaken or break the thesis.
5. Add filing clues only after those layers. For every 13F claim, show period of report, filing date, form type, calendar-day lag, and original URL.
6. Name the next concrete event that requires a review, such as an earnings release, guidance update, maturity, regulatory decision, or customer event.

## Output

Use this compact format unless the user requests another. Keep the conclusion conditional.

```text
研究结论：值得深入跟踪 / 仅在某估值区间下有安全边际 / 估值不便宜 / 证据不足
数据截止：……
来源：……

公司与财务质量
- ……

估值与进入条件
- 保守 / 基准 / 乐观区间：……
- 当前价格相对区间的位置：……
- 关键假设与不确定项：……

持仓线索
- 报告期、提交日、文件类型、滞后天数、原始链接：……

主要风险与论点失效条件
- ……

下次必须复核
- ……
```

Allowed conclusion example: "If free-cash-flow yield remains above the stated threshold in the conservative case, it merits deeper research." Forbidden: "Buy a 10% position" or a target price presented as exact.

## Hard boundaries

- A 13F is a quarter-end snapshot, not a real-time portfolio, a complete portfolio, or proof of a current holding.
- Call `value / shares` only the "implied quarter-end price." Never call it an institutional purchase price, average cost, or cost basis.
- A new position or changed share count only means two snapshots differ. Do not infer trade date, all transaction prices, or the position after the filing date.
- Do not call a share-count change an active purchase until splits, CUSIP changes, renamed issuers, and duplicated manager reports have been checked.
- A `13F-HR/A` supersedes the filing it amends. A `13F-NT` is a notice, not a holdings table.
- Options rows mostly identify the underlying security. Do not treat option quantity as common-stock ownership.
- Shared holdings can be reported by more than one manager. State the aggregation method before adding rows.
- Do not build or redistribute a CUSIP-to-ticker mapping database. Keep an identifier only with its original filing context.
