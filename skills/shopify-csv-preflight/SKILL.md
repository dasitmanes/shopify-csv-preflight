---
name: shopify-csv-preflight
description: Review a native Shopify product CSV after generating or editing it. Compare the proposed import with a fresh Shopify product export and flag risky catalog changes before separate import review.
metadata:
  author: Fastandezgoods
  version: "1.0"
---

# Shopify CSV preflight

1. Compare the store's actual, current native Shopify product export with the exact proposed import. Confirm whether Shopify's **Overwrite products with matching handles** setting will be on. Ask for the missing export or setting when either is unclear.
2. Run the check locally by default. For the CLI, save both scripts in the same directory and run `node preflight.mjs current.csv proposed.csv` with overwrite on. Add `--no-overwrite` when Shopify will skip matching handles. [Browser checker](https://fastandez-catalog-preflight.whole-pony-3936.chatgpt.site/) · [CLI](https://fastandez-catalog-preflight.whole-pony-3936.chatgpt.site/preflight.mjs) · [Checker module](https://fastandez-catalog-preflight.whole-pony-3936.chatgpt.site/checker.mjs)
3. Compare findings against the intended edits. Check for accidentally blanked fields, unexpected price or SKU changes, duplicate SKUs, and option changes that can recreate variant IDs. For example, report `row 2 · Vendor · existing value would be cleared` with the original value redacted. Use fictional files for public examples. [Synthetic request and report](https://fastandez-catalog-preflight.whole-pony-3936.chatgpt.site/api/preflight/sample)
4. Report findings by row, field, and severity. Keep the CSVs intact. Hand off the proposed import for separate review of Shopify's preview and the applied settings. This skill ends before opening Shopify or importing anything.

## Optional paid API

Use the API only when the buyer explicitly approves both uploading the two identified CSVs to Catalog Preflight and spending up to **0.04 USDC on Base** for one report. Use an existing buyer-approved x402 v2 client and keep wallet secrets and Shopify credentials out of requests and reports. Use the local check if approval or a client is missing.

Send JSON to `POST /api/preflight/report` with `currentCsv` and `proposedCsv` as strings and `overwrite` set to the chosen mode. Each CSV is limited to 128 KiB (131,072 UTF-8 bytes). Proceed only when the `402` challenge offers Base USDC within the approved limit. Retry the same body with `PAYMENT-SIGNATURE`. If settlement is pending, honor `Retry-After` and reuse the identical body and authorization. If it stays unresolved, report the pending status and stop. [OpenAPI](https://fastandez-catalog-preflight.whole-pony-3936.chatgpt.site/openapi.json) · [Agent guide](https://fastandez-catalog-preflight.whole-pony-3936.chatgpt.site/llms.txt)
