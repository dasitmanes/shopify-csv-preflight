# Shopify CSV Import Preflight

A free browser check by **Fastandezgoods** for merchants, agencies, and agents preparing a Shopify product CSV import. Compare your current Shopify export with the proposed file to catch unintended price changes, blank fields that could overwrite existing values, duplicate SKUs, and variant changes before you import. The browser check reads the files locally.

[Open the free checker](https://fastandez-catalog-preflight.whole-pony-3936.chatgpt.site/) · [Supplier price update guide](https://fastandez-catalog-preflight.whole-pony-3936.chatgpt.site/shopify-supplier-price-import.html)

## Try an example

Download [current.csv](examples/current.csv) and [proposed.csv](examples/proposed.csv), load both in the checker, and turn on overwrite. This fictional pair includes an accidentally blank vendor, a price change, and a renamed variant option for the same SKU. [See the expected report](https://fastandez-catalog-preflight.whole-pony-3936.chatgpt.site/api/preflight/sample).

## Add it to an agent workflow

Agents that support the Skills CLI can install the instructions with:

```sh
npx skills add dasitmanes/shopify-csv-preflight --skill shopify-csv-preflight
```

The [skill](skills/shopify-csv-preflight/SKILL.md) covers the free local check and how to review findings. It stops before the Shopify import. For workflow builders, there is also an [n8n recipe](https://fastandez-catalog-preflight.whole-pony-3936.chatgpt.site/shopify-csv-n8n.md).

An optional [JSON API](https://fastandez-catalog-preflight.whole-pony-3936.chatgpt.site/openapi.json) returns the same style of report for 0.04 USDC per call on Base. It requires the buyer’s approval to send files and pay.

An independent tool by Fastandezgoods.
