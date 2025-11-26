# Paid Advertising Campaign Workflow Instructions

## Overview

Complete workflow for launching and optimizing paid advertising campaigns across platforms (Google Ads, Facebook/Meta, etc.).

## Prerequisites

- Advertising platform accounts set up
- Budget allocated
- Landing pages ready
- Conversion tracking configured

## Workflow Steps

### Step 1: Define Campaign Strategy (Paid Ads Specialist)

**Objective:** Plan campaign structure and objectives.

**Actions:**
1. Define campaign objective (awareness, traffic, conversions)
2. Set budget and bidding strategy
3. Choose platforms and placements
4. Define success metrics

**Output:** `campaign_strategy`

---

### Step 2: Build Audience Targeting (Paid Ads Specialist)

**Objective:** Define target audiences for the campaign.

**Actions:**
1. Create core audiences (demographics, interests)
2. Build custom audiences (website visitors, email lists)
3. Create lookalike audiences
4. Define exclusion audiences

**Input:** `campaign_strategy`
**Output:** `audience_config`

---

### Step 3: Create Ad Copy (Content Writer)

**Objective:** Write compelling ad copy variations.

**Actions:**
1. Write primary text/headlines
2. Create description variations
3. Develop CTA options
4. Provide creative direction

**Input:** `campaign_strategy`
**Output:** `ad_copy_drafts`

**Templates:** Use `facebook-ad-tmpl.yaml` or `google-ads-tmpl.yaml`

---

### Step 4: Review Ads (Paid Ads Specialist)

**Objective:** Ensure ads meet platform requirements and best practices.

**Actions:**
1. Check ad policy compliance
2. Verify character limits
3. Review landing page alignment
4. Approve final versions

**Input:** `ad_copy_drafts`
**Output:** `final_ads`

**Checklist:** Use `paid-ads-checklist.md`

---

### Step 5: Configure Tracking (Analytics & Automation Specialist)

**Objective:** Set up conversion tracking and attribution.

**Actions:**
1. Configure pixel/tag implementation
2. Set up conversion events
3. Define attribution model
4. Create reporting dashboard

**Input:** `campaign_strategy`
**Output:** `tracking_config`

---

### Step 6: Launch Campaign (Paid Ads Specialist)

**Objective:** Launch and monitor campaign.

**Actions:**
1. Upload ads and configure targeting
2. Set budgets and schedules
3. Launch campaign
4. Monitor initial performance

**Inputs:** `final_ads`, `audience_config`, `tracking_config`
**Output:** `live_campaign`

**Checklist:** Use `campaign-launch-checklist.md`

---

## Quality Gates

- [ ] Ad copy approved
- [ ] Targeting verified
- [ ] Tracking confirmed working
- [ ] Budget limits set
- [ ] Landing pages tested

## Output Artifacts

- Campaign strategy document
- Audience targeting configuration
- Final ad copy and creative
- Tracking setup documentation
- Live campaign confirmation

## Related Workflows

- `*content-campaign` - For landing page content
- `*analytics-setup` - For advanced tracking
