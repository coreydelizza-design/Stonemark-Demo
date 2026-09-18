# IP inventory for this repository

What is in this repo, who owns it, and what protects it. Keep it current: this is the
list a lawyer, an insurer or a buyer asks for first.

| Asset | Type | Owner | Protection | Registered |
|---|---|---|---|---|
| Demo application source | Literary work (code) | Stonemark | Copyright, proprietary licence, private repo | No — see `COPYRIGHT_REGISTRATION.md` |
| Portal UI design, card anatomy, dot matrix presentation | Visual and functional design | Stonemark | Copyright, trade dress over time | No |
| The mason's mark and STONEMARK wordmark | Trademarks | Stonemark | Common-law use; intent-to-use filing planned, Classes 9 and 42 | No |
| Guide copy, report wording, findings text | Literary work | Stonemark | Copyright | No |
| Synthetic Acme dataset | Compilation | Stonemark | Copyright in the compilation and its expression | No |
| "Letter of Assessment" as a product name | Possible mark | Stonemark | [PENDING: counsel view] | No |
| The assurance method, scoring model, caps, reconciliation rules | Trade secret | Stonemark | Trade secret, held **outside** this repo | Not applicable |
| Dependencies and fonts | Third party | Their owners | Their licences — `THIRD_PARTY_NOTICES.md` | Not applicable |

## What is deliberately absent

The method. This repo demonstrates what the product produces, not how it decides. Keeping
the scoring model, caps, thresholds, reconciliation rules and requirement packs out of
this repository is what lets the demo be shown widely while the moat stays closed.

## Before making this repo public

All of the following must be true, and the answers recorded in `CHAIN_OF_TITLE.md`:

1. Full history is clean: no credential, no real data, no method material in any commit,
   not merely in the current files.
2. `THIRD_PARTY_NOTICES.md` is complete, with every required notice reproduced.
3. Every source file carries the header.
4. `DEMO_TERMS.md` has been reviewed by counsel, including the logging sentence.
5. Invented carrier and client names have been checked against real companies in the same
   sector.
6. The owner has decided, in writing, that publishing the source adds more than it costs.
   The default answer is no: the hosted demo can be public while the source stays
   private, and that combination gives away nothing.

## Review

Update this file whenever an asset class is added, and before any release, insurance
application, or conversation with an investor or acquirer.

© 2026 Stonemark Infrastructure Assurance LLC. Confidential and proprietary.
