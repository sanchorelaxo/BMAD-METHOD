# Email Sequence Workflow Instructions

## Overview

Complete workflow for creating automated email sequences from strategy to deployment.

## Prerequisites

- Target audience segment defined
- Sequence goal identified
- Email platform access

## Workflow Steps

### Step 1: Define Sequence Strategy (Email Marketer)

**Objective:** Plan the email sequence structure and goals.

**Actions:**
1. Define sequence type (welcome, nurture, cart recovery, etc.)
2. Set sequence objectives and KPIs
3. Map email cadence and timing
4. Define trigger conditions

**Output:** `sequence_plan`

**Template:** Use `email-campaign-tmpl.yaml`

---

### Step 2: Write Email Copy (Email Marketer)

**Objective:** Create email content for each message in sequence.

**Actions:**
1. Write subject lines (with A/B variants)
2. Create preview text
3. Draft email body copy
4. Define CTAs for each email

**Input:** `sequence_plan`
**Output:** `email_drafts`

**Template:** Use `drip-sequence-tmpl.yaml`

---

### Step 3: Review and Optimize Copy (Content Writer)

**Objective:** Ensure email copy is compelling and on-brand.

**Actions:**
1. Review headline effectiveness
2. Check persuasion elements
3. Verify brand voice consistency
4. Optimize CTAs

**Input:** `email_drafts`
**Output:** `reviewed_emails`

**Checklist:** Use `email-quality-checklist.md`

---

### Step 4: Configure Automation (Analytics & Automation Specialist)

**Objective:** Set up automation workflow in email platform.

**Actions:**
1. Configure trigger conditions
2. Set up email timing and delays
3. Define branching logic
4. Configure personalization tokens

**Inputs:** `sequence_plan`, `reviewed_emails`
**Output:** `automation_config`

---

### Step 5: Test and Validate (Email Marketer)

**Objective:** Ensure sequence works correctly before launch.

**Actions:**
1. Send test emails
2. Verify trigger logic
3. Check personalization
4. Review deliverability

**Input:** `automation_config`
**Output:** `test_results`

**Checklist:** Use `deliverability-checklist.md`

---

## Quality Gates

- [ ] Subject lines tested for deliverability
- [ ] Personalization tokens verified
- [ ] Unsubscribe links working
- [ ] Mobile rendering checked

## Output Artifacts

- Sequence strategy document
- Email copy for all messages
- Automation configuration
- Test results and approval

## Related Workflows

- `*content-campaign` - For content to promote via email
- `*analytics-setup` - For tracking configuration
