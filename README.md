# US Equity Investment Research

[中文说明](README.zh-CN.md)

`us-equity-investment-research` is a local instruction skill for studying one US-listed security at a time. It produces a dated research card covering business quality, valuation conditions, downside risk, and filing clues.

The skill is for education and research. It is not investment, legal, tax, or accounting advice, and it does not create an advisory relationship. It does not provide short-term signals, position sizes, or instructions to buy, sell, or trade. See [DISCLAIMER.md](DISCLAIMER.md).

## What a research card answers

1. Does the company deserve a place on a research list?
2. Which valuation conditions would justify staged consideration, rather than a false-precision buy price?
3. What is the main downside, and does it fit the valuation margin of safety?
4. Which assumptions support the thesis, and which events require a reassessment?

Form 13F is only a historical clue about institutional attention. It cannot determine an entry point or reconstruct a manager's cost.

## Install locally

Copy this directory to `$CODEX_HOME/skills/us-equity-investment-research`, or to `~/.codex/skills/us-equity-investment-research` when `CODEX_HOME` is unset. Restart or refresh Codex if the new skill does not appear. Invoke it explicitly with `$us-equity-investment-research`.

This package contains instructions only. It does not include a scraper, database, API key, personal watchlist, paid-data cache, or CUSIP mapping database.

## Data boundaries

- Original EDGAR filings are the only primary source for 13F holdings facts.
- Every 13F statement must show the period of report, filing date, form type, calendar-day lag, and original URL.
- Missing prices, estimates, or filings remain missing. The skill must not invent them.
- Apache-2.0 covers this code and documentation. It does not license market data, exchange data, or the CUSIP database.

## Layout

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

## License

[Apache License 2.0](LICENSE)
