# Content Marketing Campaign Workflow Instructions

## Overview

End-to-end pipeline for planning, creating, and optimizing content marketing campaigns using the BMAD™ Marketing team.

## Prerequisites

- Brand guidelines (recommended)
- Target audience definition
- Business goals for the campaign

## Workflow Steps

### Step 1: Define Content Strategy (Content Writer)

**Objective:** Create campaign brief defining goals, audience, and messaging.

**Actions:**
1. Define campaign objectives and KPIs
2. Identify target audience and personas
3. Develop key messaging and positioning
4. Outline content themes and topics

**Output:** `campaign_brief`

**Template:** Use `campaign-brief-tmpl.yaml`

---

### Step 2: Conduct Keyword Research (SEO Specialist)

**Objective:** Research and map keywords for content optimization.

**Actions:**
1. Expand seed keywords
2. Analyze search volume and difficulty
3. Classify search intent
4. Create keyword clusters and mapping

**Input:** `campaign_brief`
**Output:** `keyword_map`

**Template:** Use `keyword-map-tmpl.yaml`

---

### Step 3: Create Content Calendar (Content Writer)

**Objective:** Plan content production schedule.

**Actions:**
1. Map content to keywords
2. Define content types and formats
3. Set publication schedule
4. Assign production milestones

**Inputs:** `campaign_brief`, `keyword_map`
**Output:** `content_calendar`

**Template:** Use `content-calendar-tmpl.yaml`

---

### Step 4: Create Content Pieces (Content Writer)

**Objective:** Produce content according to calendar.

**Actions:**
1. Draft content following templates
2. Incorporate keywords naturally
3. Include CTAs and internal links
4. Apply brand voice guidelines

**Input:** `content_calendar`
**Output:** `content_pieces`

**Template:** Use `blog-post-tmpl.yaml`

---

### Step 5: Optimize for SEO (SEO Specialist)

**Objective:** Ensure content is search-optimized.

**Actions:**
1. Review keyword placement
2. Optimize meta titles and descriptions
3. Check internal/external linking
4. Validate technical SEO elements

**Input:** `content_pieces`
**Output:** `optimized_content`

**Checklist:** Use `seo-content-checklist.md`

---

### Step 6: Plan Social Distribution (Social Media Manager)

**Objective:** Create social promotion plan for content.

**Actions:**
1. Adapt content for each platform
2. Create social copy variations
3. Schedule posts
4. Plan engagement tactics

**Input:** `optimized_content`
**Output:** `social_plan`

---

### Step 7: Set Up Tracking (Analytics & Automation Specialist)

**Objective:** Configure analytics and tracking.

**Actions:**
1. Set up UTM parameters
2. Configure conversion tracking
3. Create performance dashboard
4. Define reporting schedule

**Input:** `campaign_brief`
**Output:** `tracking_config`

---

## Quality Gates

Before proceeding to each step, verify:

- [ ] Previous step deliverables complete
- [ ] Alignment with campaign objectives
- [ ] Brand guidelines followed

## Output Artifacts

- Campaign brief document
- Keyword research and mapping
- Content calendar
- Content pieces (optimized)
- Social distribution plan
- Tracking configuration

## Related Workflows

- `*seo-optimization` - For deep SEO work
- `*social-media-launch` - For social distribution
- `*email-sequence` - For email promotion

## Reference Data

- `content-frameworks.md` - Content strategy frameworks
- `headline-formulas.md` - Proven headline patterns
