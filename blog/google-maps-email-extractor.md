---
layout: default
title: How to Extract Business Emails from Google Maps (Free Guide)
description: Step-by-step guide to extracting business emails, phone numbers, and contact info from Google Maps for lead generation. No coding required.
---

# How to Extract Business Emails from Google Maps (No Code, Free)

Need business leads fast? Google Maps is the biggest database of local businesses — and you can extract emails, phone numbers, and websites from it **without writing a single line of code**.

## Why Google Maps for Lead Generation?

- **250M+ businesses** listed worldwide
- **Contact info included** — emails, phones, websites
- **Location-based filtering** — target any city or country
- **Category filtering** — restaurants, dentists, SaaS companies...

## The Tool: Google Maps Email Extractor

I built a [Google Maps Email Extractor](https://apify.com/intelligent_yaffle/google-maps-email-extractor) that does all the work:

| Data Field | Example |
|-----------|--------|
| Business name | Joe's Coffee Shop |
| Email | joe@joescoffee.com |
| Phone | +1-555-0123 |
| Website | joescoffee.com |
| Address | 123 Main St, NYC |
| Rating | 4.5 stars |
| Review count | 128 reviews |

## Step-by-Step Guide

### Step 1: Define Your Search

Think about what you'd search on Google Maps:
- "dentists in Los Angeles"
- "SaaS companies in San Francisco"
- "restaurants in London"

### Step 2: Run the Extractor

1. Go to [Google Maps Email Extractor](https://apify.com/intelligent_yaffle/google-maps-email-extractor)
2. Enter your search query
3. Set the maximum number of results
4. Click **Start**

### Step 3: Download Your Leads

Results come in JSON, CSV, or Excel. Each row is a business with all contact info.

## API Integration

```python
from apify_client import ApifyClient

client = ApifyClient('YOUR_TOKEN')
run = client.actor('intelligent_yaffle/google-maps-email-extractor').call(
    run_input={'searchQuery': 'marketing agencies in New York', 'maxResults': 500}
)
for lead in client.dataset(run['defaultDatasetId']).iterate_items():
    if lead.get('email'):
        print(f"{lead['name']} — {lead['email']}")
```

## More Lead Gen Tools

- [B2B Leads Finder](https://apify.com/intelligent_yaffle/leads-finder) — Extract emails from company websites
- [Website Contact Finder](https://apify.com/intelligent_yaffle/website-contact-finder) — Get contacts from any URL
- [Email Validator](https://apify.com/intelligent_yaffle/email-validator) — Verify emails before sending

Full catalog: [apify.com/intelligent_yaffle](https://apify.com/intelligent_yaffle)

---

[← Back to all scrapers](../)
