# Email Analytics & Metrics

## Key Performance Indicators (KPIs)

### Delivery Metrics
- **Delivery Rate**: Percentage of emails successfully delivered to recipient mail servers
  - Target: > 98%
  - Formula: (Delivered / Sent) × 100
- **Bounce Rate**: Percentage of emails that could not be delivered
  - Hard Bounces: Permanent failures (invalid address) — remove immediately
  - Soft Bounces: Temporary failures (full mailbox) — retry up to 3 times
  - Acceptable threshold: < 2% total bounce rate

### Engagement Metrics
- **Open Rate**: Percentage of delivered emails that were opened
  - Industry average: 20–25% (varies by sector)
  - Note: Apple MPP inflates open rates; treat as directional, not absolute
  - Formula: (Unique Opens / Delivered) × 100
- **Click-Through Rate (CTR)**: Percentage of delivered emails with at least one click
  - Industry average: 2–5%
  - Formula: (Unique Clicks / Delivered) × 100
- **Click-to-Open Rate (CTOR)**: Clicks relative to opens — measures content relevance
  - Target: > 15%
  - Formula: (Unique Clicks / Unique Opens) × 100
- **Unsubscribe Rate**: Percentage of recipients who opted out
  - Acceptable threshold: < 0.5% per campaign
  - High rates signal poor list hygiene or irrelevant content

### Conversion Metrics
- **Conversion Rate**: Percentage of recipients who completed a desired action
  - Formula: (Conversions / Delivered) × 100
- **Revenue Per Email (RPE)**: Total revenue attributed to a campaign divided by emails sent
- **Return on Investment (ROI)**: (Revenue - Cost) / Cost × 100

### Reputation Metrics
- **Spam Complaint Rate**: Percentage of recipients who marked email as spam
  - Critical threshold: Keep below 0.1% (Google/Yahoo requirement as of 2024)
  - Formula: (Spam Complaints / Delivered) × 100
- **List Growth Rate**: Net growth of your email list over time
  - Formula: ((New Subscribers - Unsubscribes) / Total List Size) × 100

---

## Tracking Implementation

### Open Tracking
- Uses a 1×1 transparent pixel embedded in the email HTML
- Fires a request to your tracking server when the image loads
- Limitations: Blocked by image-disabled clients, Apple MPP caches opens server-side

### Click Tracking
- Redirect all links through a tracking URL before forwarding to the destination
- Example: `https://track.yourdomain.com/click?id=abc123&url=https://yourdomain.com/product`
- Ensure tracking domains are authenticated (DKIM/SPF aligned) to avoid spam filters

### UTM Parameters
Append UTM parameters to all links for Google Analytics / downstream attribution:
```
utm_source=email
utm_medium=newsletter (or transactional, promotional, etc.)
utm_campaign=campaign-name
utm_content=cta-button (optional, for A/B testing)
```

---

## A/B Testing Guidelines

### What to Test
- Subject lines (most impactful on open rate)
- Preview text / preheader
- Send time and day of week
- From name / sender identity
- CTA button copy, color, and placement
- Email length and content structure
- Personalization depth

### Testing Best Practices
- Test one variable at a time
- Use a statistically significant sample size (minimum 1,000 recipients per variant)
- Run tests for at least 4 hours before declaring a winner
- Use 80/20 split (80% test, 20% held for winner send) for time-sensitive campaigns
- Document all test results for institutional knowledge

---

## Reporting Cadence

| Report Type     | Frequency  | Audience          | Key Metrics                          |
|-----------------|------------|-------------------|--------------------------------------|
| Campaign Report | Per send   | Marketing team    | Open, CTR, conversions, revenue      |
| Weekly Digest   | Weekly     | Marketing manager | Trend lines, list growth, complaints |
| Monthly Review  | Monthly    | Leadership        | ROI, deliverability health, KPI vs target |
| Quarterly Audit | Quarterly  | All stakeholders  | List hygiene, suppression review, strategy |

---

## Benchmarks by Email Type

| Email Type        | Avg Open Rate | Avg CTR | Avg Unsubscribe Rate |
|-------------------|---------------|---------|----------------------|
| Welcome           | 50–60%        | 14–25%  | 0.1–0.3%             |
| Transactional     | 40–50%        | 10–20%  | < 0.1%               |
| Newsletter        | 20–30%        | 2–5%    | 0.2–0.5%             |
| Promotional       | 15–25%        | 2–4%    | 0.3–0.5%             |
| Re-engagement     | 10–15%        | 1–3%    | 0.5–1.0%             |
| Abandoned Cart    | 35–45%        | 8–15%   | 0.2–0.4%             |

---

## Actionable Thresholds

- **Open Rate drops > 20% week-over-week**: Investigate subject line quality, sender reputation, or deliverability issues
- **CTR drops > 30%**: Review content relevance, CTA placement, and segmentation
- **Spam complaints > 0.08%**: Pause campaign, audit list quality and consent records
- **Bounce rate > 5%**: Halt sends, perform list hygiene, investigate data source
- **Unsubscribe rate > 1%**: Reassess send frequency, content relevance, and audience segmentation
