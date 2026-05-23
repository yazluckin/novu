# Email Testing Best Practices

Testing emails before sending ensures deliverability, rendering consistency, and campaign effectiveness.

## Pre-Send Testing Checklist

### Content Review
- [ ] Proofread all copy for spelling and grammar errors
- [ ] Verify all links are functional and point to the correct destinations
- [ ] Confirm unsubscribe link is present and working
- [ ] Check that all personalization tokens have fallback values
- [ ] Validate that dynamic content renders correctly for all segments
- [ ] Ensure subject line and preview text are compelling and accurate

### Technical Validation
- [ ] Test HTML renders correctly across major email clients
- [ ] Verify plain-text version is present and readable
- [ ] Confirm images have descriptive alt text
- [ ] Check that image file sizes are optimized (< 200KB per image)
- [ ] Validate total email size is under 102KB to avoid Gmail clipping
- [ ] Test that CTA buttons are tappable on mobile (minimum 44x44px)

## A/B Testing

### What to Test

**Subject Lines**
- Length (short vs. long)
- Personalization (with vs. without recipient name)
- Tone (formal vs. casual)
- Emoji usage
- Question vs. statement format
- Urgency indicators

**Send Time**
- Day of week
- Time of day
- Timezone optimization

**Content Elements**
- CTA button text and color
- Email length (short vs. long form)
- Single vs. multiple CTAs
- Image-heavy vs. text-heavy layouts
- Personalized vs. generic content

**From Name**
- Company name vs. individual name
- "Team at Company" format

### A/B Test Setup Guidelines

```
Minimum sample size per variant: 1,000 recipients
Test duration: 2–4 hours for time-sensitive metrics (opens)
                24–72 hours for conversion metrics
Confidence threshold: 95% statistical significance before declaring a winner
Test one variable at a time for clear attribution
```

## Email Client Testing

### Priority Clients to Test (by market share)

| Client | Platform | Market Share |
|--------|----------|--------------|
| Apple Mail | iOS/macOS | ~55% |
| Gmail | Web/Android/iOS | ~28% |
| Outlook | Windows | ~6% |
| Yahoo Mail | Web/Mobile | ~3% |
| Samsung Mail | Android | ~2% |

### Known Rendering Issues

**Outlook (Windows)**
- Uses Microsoft Word rendering engine
- Limited CSS support (no `flexbox`, `grid`, `CSS animations`)
- Use table-based layouts for reliable rendering
- Background images require VML fallback

**Gmail**
- Clips emails exceeding 102KB
- Strips `<style>` blocks in some versions — use inline CSS
- Supports media queries in modern versions

**Apple Mail**
- Excellent CSS support
- Auto-detects phone numbers and dates — may alter styling
- Dark mode support requires `prefers-color-scheme` media query

## Spam Testing

### Spam Score Factors
- Spam trigger words in subject line or body
- Image-to-text ratio (aim for 60% text, 40% images)
- Missing or broken unsubscribe link
- Sending from a domain without SPF/DKIM/DMARC records
- High complaint rates from previous campaigns
- Purchased or unverified email lists

### Recommended Spam Testing Tools
- **Mail-Tester** (mail-tester.com) — free spam score checker
- **GlockApps** — inbox placement testing across ISPs
- **Litmus Spam Testing** — integrated with design preview
- **MXToolbox** — DNS record validation (SPF, DKIM, DMARC)

## Rendering Preview Tools

- **Litmus** — 100+ client previews, accessibility checks
- **Email on Acid** — client previews with automated QA
- **Testi@** — free limited previews

## Accessibility Testing

- Use a minimum font size of 14px for body text
- Ensure color contrast ratio meets WCAG AA (4.5:1 for normal text)
- Test with screen readers (NVDA, VoiceOver)
- Verify logical reading order in plain-text version
- Avoid using color alone to convey meaning

## Post-Send Monitoring

Monitor these metrics in the first 24–48 hours after send:

| Metric | Healthy Range | Action if Outside Range |
|--------|--------------|-------------------------|
| Open Rate | 20–40% | Review subject line and sender reputation |
| Click Rate | 2–5% | Audit CTA placement and copy |
| Bounce Rate | < 2% | Clean list, check domain health |
| Unsubscribe Rate | < 0.5% | Review content relevance and frequency |
| Spam Complaint Rate | < 0.08% | Audit list quality and opt-in process |

## Related Resources
- [Analytics](./analytics.md)
- [Deliverability](./deliverability.md)
- [Personalization](./personalization.md)
