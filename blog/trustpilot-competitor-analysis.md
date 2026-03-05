---
layout: default
title: How to Scrape Competitor Reviews from Trustpilot, G2, and Google (2026 Guide)
description: Learn how to monitor competitor reviews from Trustpilot, G2, Google Reviews automatically. Extract ratings, sentiment, and trends.
---

# How to Scrape Competitor Reviews from Trustpilot, G2, and Google

Your competitors' reviews are public. They contain exactly what customers love and hate. Here's how to extract and analyze them.

## Why Monitor Competitor Reviews?

- **Find pain points** — What customers complain about = your opportunity
- **Track sentiment** — Is satisfaction going up or down?
- **Spot feature gaps** — What features do customers wish they had?
- **Sales intelligence** — Use unhappy competitor reviews in your pitch

## Review Platform Scrapers

| Platform | Best For | Link |
|----------|----------|------|
| Trustpilot | E-commerce, SaaS | [Scraper](https://apify.com/intelligent_yaffle/trustpilot-scraper) |
| G2 | B2B software | [Scraper](https://apify.com/intelligent_yaffle/g2-reviews-scraper) |
| Google Reviews | Local businesses | [Scraper](https://apify.com/intelligent_yaffle/google-reviews-scraper) |
| Capterra | Software | [Scraper](https://apify.com/intelligent_yaffle/capterra-scraper) |
| Yelp | Restaurants, local | [Scraper](https://apify.com/intelligent_yaffle/yelp-business-scraper) |
| Glassdoor | Employer reviews | [Scraper](https://apify.com/intelligent_yaffle/glassdoor-reviews-scraper) |

## Automated Competitor Analysis with Python

```python
from apify_client import ApifyClient

client = ApifyClient('YOUR_TOKEN')

competitors = [
    'https://trustpilot.com/review/competitor1.com',
    'https://trustpilot.com/review/competitor2.com',
]

for url in competitors:
    run = client.actor('intelligent_yaffle/trustpilot-scraper').call(
        run_input={'startUrls': [{'url': url}], 'maxItems': 200}
    )
    reviews = list(client.dataset(run['defaultDatasetId']).iterate_items())
    ratings = [r['rating'] for r in reviews if r.get('rating')]
    avg = sum(ratings) / len(ratings) if ratings else 0
    negative = len([r for r in ratings if r <= 2])
    print(f"{url}: Avg {avg:.1f}/5, {negative} negative reviews")
```

## Use Cases

**For Sales Teams:** "I noticed your competitor has 23% negative reviews about shipping delays. Our platform guarantees 2-day delivery..."

**For Product Teams:** "45% of 1-star reviews mention difficult onboarding. Let's make ours 10x simpler."

**For Marketing:** "Competitor A dropped from 4.5 to 3.8 stars. Time for a comparison campaign."

---

All 100 scrapers: [apify.com/intelligent_yaffle](https://apify.com/intelligent_yaffle)

[← Back to home](../)
