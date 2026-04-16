# TikTok Shop Affiliate Intelligence

Find which creators are promoting any TikTok Shop product. Get verified product details, affiliate creator names, follower counts, and sales data. No login required.

## The Question This Answers

**"If I have a TikTok Shop product, who is actually promoting it, and is it worth paying attention to?"**

This actor gives you a real answer with verified data:

- Product name, price, sales count, rating
- Which creators are actively promoting it
- Creator follower counts and profile URLs
- Whether the product has real affiliate momentum

## Who Uses This

**TikTok Shop sellers** check whether a product already has affiliate momentum before investing in inventory or ads.

**Affiliate managers** at agencies see which creators are pushing a product and whether they should recruit or avoid them.

**Product researchers** compare competitor products by affiliate activity. More active affiliates usually means a winning product.

**Freelancers** use this as a backend for TikTok Shop research gigs. Run the actor for $0.05, deliver a report for $200.

## How It Works

```
Product URL  -->  Verified Product Data  -->  Creator Detection  -->  Structured Output
                  (name, price, sales)       (who promotes it)       (JSON / CSV / Excel)
```

1. Pass a TikTok Shop product URL
2. The actor verifies the product through multiple data sources
3. Detects the creator/affiliate promotion block
4. Returns structured data with verified status

No cookies. No login. No account risk.

## Input

```json
{
  "productUrl": "https://www.tiktok.com/view/product/1234567890"
}
```

Or search for products by keyword:

```json
{
  "searchQuery": "skincare serum",
  "maxProducts": 5
}
```

| Parameter | Type | Description |
|-----------|------|-------------|
| productUrl | String | Direct TikTok Shop product URL |
| searchQuery | String | Search TikTok Shop by keyword |
| maxProducts | Number | Max products to analyze (default 5) |

## Output

```json
{
  "product": {
    "name": "Vitamin C Brightening Serum",
    "price": "$12.99",
    "salesCount": 45000,
    "rating": 4.8,
    "url": "https://www.tiktok.com/view/product/1234567890"
  },
  "affiliates": [
    {
      "username": "@skincarebyjess",
      "profileUrl": "https://www.tiktok.com/@skincarebyjess",
      "followers": 850000,
      "salesCount": 2300
    },
    {
      "username": "@glowupqueen",
      "profileUrl": "https://www.tiktok.com/@glowupqueen",
      "followers": 420000,
      "salesCount": 1100
    }
  ],
  "dataSource": "verified_success",
  "scrapedAt": "2026-04-16T10:30:00.000Z"
}
```

## What "Verified" Means

Every result is tagged with its verification status:

| Status | Meaning |
|--------|---------|
| verified_success | Product and creators confirmed from live TikTok data |
| partial_verified | Product confirmed, some creator data from cached sources |
| serp_enriched | Data recovered from Google cached pages |

The actor never fakes results. If it cannot verify the data, it tells you.

## Pricing

| What you pay | Cost |
|-------------|------|
| Per product analyzed | $0.05 |

Check 20 products: $1.00. Check 100 products: $5.00.

Compare that to manual research (30 min per product at $50/hr = $25 per product).

## Use Cases

### Seller: Should I launch this product?

Check if similar products already have affiliate momentum. If 10 creators are pushing a competitor product with 50K+ sales, there is demand. If nobody is promoting it, you might be first or the product might not sell.

### Agency: Which creators should we recruit?

Search your client's product category. See who is already promoting similar products. Those creators have proven they can drive TikTok Shop sales. Recruit them instead of guessing.

### Competitor research

Check a competitor's product URL. See exactly who promotes it, how many followers those creators have, and what the sales numbers look like. Build your strategy based on data, not guesses.

### Freelancer backend

Accept TikTok Shop research gigs on Upwork or Fiverr. Run this actor for $0.05 per product. Deliver a formatted report. Charge $200+. Your margin is 99%.

## Quick Start

### Run on Apify

1. Go to [TikTok Shop Affiliate Intelligence](https://apify.com/george.the.developer/tiktok-shop-affiliate-sales-scraper)
2. Paste a product URL
3. Click Start
4. Download results as JSON, CSV, or Excel

### API

```bash
curl -X POST "https://api.apify.com/v2/acts/george.the.developer~tiktok-shop-affiliate-sales-scraper/runs" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{"productUrl": "https://www.tiktok.com/view/product/1234567890"}'
```

### Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_TOKEN")
run = client.actor("george.the.developer/tiktok-shop-affiliate-sales-scraper").call(
    run_input={"productUrl": "https://www.tiktok.com/view/product/1234567890"}
)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(f"Product: {item['product']['name']}")
    print(f"Affiliates: {len(item['affiliates'])}")
    for a in item['affiliates']:
        print(f"  @{a['username']} - {a['followers']} followers")
```

## 中文简介

### TikTok商店联盟营销情报

查询任何TikTok商店产品的推广创作者信息。获取验证过的产品数据、创作者名称、粉丝数量和销售情报。

**主要功能：**

- 输入TikTok商店产品链接，获取产品详情和推广创作者列表
- 智能多源数据验证，确保数据真实可靠
- 支持关键词搜索批量发现热门产品
- 每个产品分析仅需 $0.05

**适用场景：** TikTok商店卖家选品、联盟营销管理、竞品分析、市场调研

[在Apify商店免费试用 >>>](https://apify.com/george.the.developer/tiktok-shop-affiliate-sales-scraper)

## Related Actors

- [Influencer Marketing Intelligence](https://apify.com/george.the.developer/influencer-marketing-intel) - Find influencers across Instagram, TikTok, YouTube
- [Google Maps Lead Intel](https://apify.com/george.the.developer/google-maps-lead-intel) - Local business leads with email validation
- [AI Content Detector](https://apify.com/george.the.developer/ai-content-detector) - Detect AI generated text
- [Email Validator API](https://apify.com/george.the.developer/email-validator-api) - SMTP email verification

[View all 57 actors >>>](https://apify.com/george.the.developer)

## Support

- **Apify Store**: [TikTok Shop Affiliate Intelligence](https://apify.com/george.the.developer/tiktok-shop-affiliate-sales-scraper)
- **X/Twitter**: [@ai_in_it](https://x.com/ai_in_it)
