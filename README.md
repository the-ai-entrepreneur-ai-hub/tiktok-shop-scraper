# TikTok Shop Affiliate Sales Scraper

> Extract TikTok Shop products, affiliate commissions, sales volumes, and trending product data

[![Try on Apify](https://img.shields.io/badge/Try_on-Apify_Store-00C7B7?style=for-the-badge&logo=apify)](https://apify.com/george.the.developer/tiktok-shop-affiliate-sales-scraper)
[![GitHub](https://img.shields.io/badge/Source-GitHub-181717?style=for-the-badge&logo=github)](https://github.com/the-ai-entrepreneur-ai-hub/tiktok-shop-scraper)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

---

## Overview

TikTok Shop Affiliate Sales Scraper extracts comprehensive product data from TikTok Shop including pricing, affiliate commission rates, sales volumes, seller info, and reviews. Built for dropshippers, affiliate marketers, and e-commerce researchers who need real-time intelligence on what sells on TikTok.

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white) ![Crawlee](https://img.shields.io/badge/Crawlee-00C7B7?style=flat&logo=apify&logoColor=white) ![Puppeteer](https://img.shields.io/badge/Puppeteer-40B5A4?style=flat&logo=puppeteer&logoColor=white) ![Apify](https://img.shields.io/badge/Apify_SDK-00C7B7?style=flat&logo=apify&logoColor=white)

---

## Architecture

```mermaid
graph LR
    A["Input: Search Query / Category"] --> B["Crawlee Engine"]
    B --> C["TikTok Shop"]
    C --> D["Data Extraction"]
    D --> E["Clean & Structure"]
    E --> F["Output: JSON/CSV"]

    style A fill:#F5C542,stroke:#D4A017,color:#1a1a2e
    style B fill:#6366f1,stroke:#4338ca,color:#ffffff
    style C fill:#f97316,stroke:#c2410c,color:#ffffff
    style D fill:#8b5cf6,stroke:#6d28d9,color:#ffffff
    style E fill:#06b6d4,stroke:#0891b2,color:#ffffff
    style F fill:#34d399,stroke:#065f46,color:#1a1a2e
```

---

## How It Works

```mermaid
sequenceDiagram
    participant U as User
    participant A as TikTok Shop Affiliate Sales Scraper
    participant T as TikTok Shop
    participant D as Apify Dataset

    U->>A: Provide input (Search Query / Category)
    A->>A: Validate & configure
    A->>T: Navigate & extract data
    T-->>A: Raw HTML / JSON
    A->>A: Parse, clean & deduplicate
    A->>D: Store structured results
    D-->>U: Download JSON / CSV / Excel
```

**Step-by-step:**

1. **Input Validation** — Your configuration is validated and the scraping session is initialized with optimal proxy settings
2. **Smart Crawling** — Crawlee manages request queues, retries, and proxy rotation automatically for maximum reliability
3. **Data Extraction** — Structured data is parsed from each page using optimized selectors and anti-detection measures
4. **Deduplication** — Results are deduplicated and cleaned to ensure high data quality with no duplicates
5. **Output Delivery** — Clean, structured data is saved to your Apify dataset for download or API access

---

## Input Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `searchQuery` | `String` | Product search on TikTok Shop |
| `category` | `String` | Product category filter |
| `maxProducts` | `Number` | Maximum products to extract |
| `sortBy` | `String` | Sort: best_selling, newest, price_asc, price_desc |
| `minCommission` | `Number` | Minimum affiliate commission percentage |

### Input Example

```json
{
  "searchQuery": "kitchen gadgets",
  "category": "Home & Garden",
  "maxProducts": 100,
  "sortBy": "best_selling",
  "minCommission": 10
}
```

---

## Output Fields

| Field | Type | Description |
|-------|------|-------------|
| `productName` | `String` | Product title |
| `price` | `Number` | Current selling price |
| `originalPrice` | `Number` | Original price before discount |
| `salesCount` | `Number` | Total units sold |
| `commissionRate` | `Number` | Affiliate commission percentage |
| `sellerName` | `String` | Seller/shop name |
| `rating` | `Number` | Product rating (1-5) |
| `reviewCount` | `Number` | Number of product reviews |
| `productUrl` | `String` | Direct TikTok Shop listing link |

### Output Example

```json
{
  "productName": "Electric Vegetable Chopper 3-in-1",
  "price": 24.99,
  "originalPrice": 49.99,
  "salesCount": 15420,
  "commissionRate": 15,
  "sellerName": "KitchenPro Official",
  "rating": 4.6,
  "reviewCount": 2840,
  "productUrl": "https://shop.tiktok.com/product/abc123"
}
```

---

## Use Cases

- **Dropshipping Research** — Find trending high-margin products with proven TikTok sales velocity
- **Affiliate Marketing** — Discover products with best commission rates and sales volumes
- **Competitive Analysis** — Monitor competitor pricing and sales performance on TikTok
- **Trend Forecasting** — Track rising product categories on TikTok Shop
- **Supplier Discovery** — Find successful sellers for wholesale partnerships

---

## Data Flow

```mermaid
flowchart TD
    subgraph Input
        A["Search Query / Category"] --> B[Proxy Configuration]
        B --> C[Max Results & Filters]
    end
    subgraph Processing
        D[Smart Request Queue] --> E[Anti-Bot Handling]
        E --> F[Data Extraction]
        F --> G[Deduplication & Cleaning]
    end
    subgraph Output
        H[JSON Dataset] --> I[CSV Export]
        I --> J[API Access]
    end
    Input --> Processing --> Output

    style A fill:#F5C542,stroke:#D4A017,color:#1a1a2e
    style G fill:#06b6d4,stroke:#0891b2,color:#ffffff
    style J fill:#34d399,stroke:#065f46,color:#1a1a2e
```

---

## Pricing

This actor uses Apify's **Pay-Per-Event** pricing. You only pay for what you use.

| Event | Price | Description |
|-------|-------|-------------|
| `product-extracted` | $0.004 | Per product listing extracted |
| `seller-profiled` | $0.008 | Per seller profile analyzed |

> Free tier available on Apify. No credit card required to start.

---

## Getting Started

### Run on Apify Console

1. Go to [TikTok Shop Affiliate Sales Scraper on Apify Store](https://apify.com/george.the.developer/tiktok-shop-affiliate-sales-scraper)
2. Click **"Try for free"**
3. Configure your input parameters
4. Click **"Start"** and wait for results
5. Download your data as JSON, CSV, or Excel

### Run via API

```bash
curl -X POST "https://api.apify.com/v2/acts/george.the.developer~tiktok-shop-affiliate-sales-scraper/runs" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"searchQuery":"kitchen gadgets","category":"Home & Garden","maxProducts":100,"sortBy":"best_selling","minCommission":10}'
```

### Run with Python

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")
run = client.actor("george.the.developer/tiktok-shop-affiliate-sales-scraper").call(
    run_input={
    "searchQuery": "kitchen gadgets",
    "category": "Home & Garden",
    "maxProducts": 100,
    "sortBy": "best_selling",
    "minCommission": 10
}
)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

---

## Tech Stack

| Technology | Purpose |
|------------|---------|
| **Node.js** | Runtime environment |
| **Crawlee** | Web scraping and crawling framework |
| **Puppeteer** | Browser automation for JavaScript-rendered pages |
| **Apify SDK** | Actor lifecycle, storage, and proxy management |

---

## Related Actors

More data extraction tools by [George The Developer](https://apify.com/george.the.developer):

- [Reddit Scraper Pro](https://apify.com/george.the.developer/reddit-scraper-pro) — Extract posts, comments, user profiles, and subreddit data from Reddit at scale 
- [AI Training Data Scraper](https://apify.com/george.the.developer/ai-training-data-scraper) — Collect structured, clean datasets from the web purpose-built for training machi
- [Influencer Marketing Intel](https://apify.com/george.the.developer/influencer-marketing-intel) — Discover and analyze social media influencers with engagement metrics, audience 
- [Google Maps Leads & Website Audit](https://apify.com/george.the.developer/google-maps-leads-website-audit) — Extract business leads from Google Maps with automated website audits for contac
- [App Review Pain Miner](https://apify.com/george.the.developer/app-review-pain-miner) — Extract and analyze app store reviews to discover user pain points, feature requ

[View all actors on Apify Store >>>](https://apify.com/george.the.developer)

---

## Support

- **Apify Store**: [https://apify.com/george.the.developer/tiktok-shop-affiliate-sales-scraper](https://apify.com/george.the.developer/tiktok-shop-affiliate-sales-scraper)
- **GitHub Issues**: [Report a bug](https://github.com/the-ai-entrepreneur-ai-hub/tiktok-shop-scraper/issues)
- **Author**: [George The Developer](https://apify.com/george.the.developer)

---

## License

MIT License. See [LICENSE](LICENSE) for details.

---

*Built with Crawlee and the Apify SDK by [George The Developer](https://apify.com/george.the.developer). Star this repo if you find it useful!*
