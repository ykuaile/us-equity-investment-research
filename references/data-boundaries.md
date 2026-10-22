# Data Boundaries

Use this file before relying on EDGAR, 13F holdings, prices, estimates, or identifiers. Re-check the official page when a deadline, form, or access rule may have changed. Rules below were reviewed against SEC pages on October 22, 2026.

## Source order

1. The original SEC EDGAR `13F-HR` or `13F-HR/A`, including its accession number, filing URL, period of report, and filing date.
2. `https://data.sec.gov/submissions/CIK##########.json`, EDGAR indexes, and full-text search to discover filings. Submission JSON updates through the day; the bulk ZIP is republished around 3:00 a.m. Eastern Time.
3. The SEC's official List of Section 13(f) Securities for reportable-universe checks.
4. Issuer investor-relations materials, financial reports, and regulatory filings for fundamentals, guidance, and company actions.
5. Secondary sites such as WhaleWisdom, 13F.info, and Dataroma only for browsing, alias resolution, and cross-checking. Label their processing time and methodology.
6. Prices, consensus estimates, and valuation multiples only from a source the user is authorized to use. Record the as-of time. If unavailable, say unavailable.

EDGAR public data APIs do not require an API key. Any keyed adapter must read its secret from an environment variable. A repository may contain variable names in `.env.example`, never a real secret.

## EDGAR access

Automated access must send a descriptive User-Agent that identifies the requester, cache retrieved results, and stay within the SEC's fair-access limit of 10 requests per second. The SEC may temporarily limit an IP address above that rate. Do not bypass access controls or use an unclassified automated crawl beyond the stated policy.

The SEC does not guarantee that filings are accurate. Acceptance by EDGAR means the submission was received, not that its content is correct.

## Form 13F facts

- The filing obligation applies to an institutional investment manager that exercises investment discretion over at least $100 million in Section 13(f) securities. The threshold is tested on the last trading day of any month.
- After crossing the threshold, the manager generally makes four filings: the first within 45 days after the fourth quarter, then one within 45 days after each of the next three calendar quarters. A later drop below the threshold does not by itself end the obligation.
- A deadline that falls on a weekend or holiday moves to the next business day. SEC examples updated March 6, 2026 include May 15, 2026; August 14, 2026; November 16, 2026; and February 16, 2027 for the 2026 quarters.
- `periodOfReport` is the quarter-end snapshot date. `filingDate` is the public submission date. Show both and calculate the calendar-day lag.
- The public delay can be up to about 45 days. The manager may have changed the position completely during that period.
- `13F-HR` reports holdings or a combination report. `13F-HR/A` amends it and must be preferred to the filing it replaces. `13F-NT` is a notice, normally has no holdings table, and is not a holdings report.
- Holdings facts come from the Information Table, not a web summary. Rows generally identify the issuer, class, CUSIP, reported value, shares or principal amount, investment discretion, voting authority, and PUT or CALL where applicable.
- The current form requires values rounded to the nearest dollar. Older filings may use thousands of dollars. Preserve `value_reported`, `value_scale`, and `value_usd`; never silently rewrite the reported value.
- Report only long positions. Short stock is omitted and does not offset a long position. Securities loaned out remain reportable by the lender, not the borrower.
- A manager may report listed puts, calls, and warrants it holds, but not options it writes. Most option-row identifiers refer to the underlying security, so option quantity is not common-stock ownership.
- The same security may appear on multiple rows because of class, discretion, or shared managers. State how rows are aggregated before adding them.
- Official lists are quarterly. They primarily cover US exchange-traded stocks, closed-end funds, ETFs, and some convertible debt, warrants, and options. Open-end funds generally are not included. Securities not on the list should not appear on Form 13F.
- As updated December 29, 2025, the SEC says the official list is PDF-only historically and also TXT beginning with the fourth quarter of 2025. Do not assume an official CSV or Excel file exists.
- Splits, CUSIP changes, issuer renames, and combined reporting can create a false appearance of large buying. Do not call a share-count change an active purchase until those effects are checked.
- Another manager's reporting, combination reports, or confidential treatment can make a filing incomplete. After denial or expiration of confidential treatment, the public amendment is due within six business days.
- Common filing errors include bad CUSIPs, incorrect amendment types, and values inflated by 1,000. Keep the raw value and flag the suspicion.

## What a 13F cannot prove

- It is not a real-time holding and not proof that the position still exists.
- It is not the manager's complete portfolio. It generally omits cash, many bonds, many foreign holdings, shorts, and written options.
- `value / shares` is only an implied quarter-end price. It is commonly near the market price, not a transaction price, average acquisition price, or cost basis.
- A difference between snapshots does not reveal the trade date, every trade, or whether the position was sold after filing.
- A newly disclosed position cannot be described as "recently bought" solely because the public first sees it on the filing date.

## Market data and estimates

Use the user's legally available source and record whether a figure is a trade, quote, official close, or estimate. Do not silently reuse an old cached value. Paid and exchange data remain under their own licenses and are not redistributable merely because research notes are open source.

## Identifiers and redistribution

A CUSIP printed in an original 13F is part of that filing. CUSIP Global Services states that the CUSIP database, standard descriptions, and related data are licensed intellectual property, and that use of CUSIP numbers and descriptions must not create or substitute for a CUSIP master file. Do not include a complete or continuously updated CUSIP-to-ticker or issuer mapping in a repository, package, or public API. A user may configure a lawful mapping or market-data provider. A small number of identifiers may remain attached to their original SEC source, but they must not become a substitute database.

## Missing data

State the missing field, why it blocks the conclusion, and which source would resolve it. Separate known facts from estimates and inferences. A conditional research conclusion is allowed only when its assumptions and missing inputs are visible.
