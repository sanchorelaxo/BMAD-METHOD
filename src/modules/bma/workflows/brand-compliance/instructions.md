# Brand Compliance Review Workflow Instructions

## Overview

This workflow coordinates multiple specialist agents to conduct comprehensive brand compliance audits across all marketing channels and mediums. The Brand Compliance Manager serves as the primary coordinator, orchestrating reviews by specialists in visual design, content, social media, video, email, advertising, and digital/SEO.

## Prerequisites

### Brand Guidelines Documentation

Before running this workflow, ensure brand guidelines are documented in MD files in your project root. The workflow automatically searches for:

- `*brand*.md` - Brand guidelines, brand book
- `*style*.md` - Style guides
- `*guideline*.md` - General guidelines
- `*identity*.md` - Visual identity documentation
- `*compliance*.md` - Compliance requirements
- `*standards*.md` - Brand standards
- `README.md` - Project readme (may contain brand info)

### Recommended Brand Documentation Structure

Create a `brand-guidelines.md` file in your project root containing:

```markdown
# Brand Guidelines

## Brand Identity
- Brand name and variations
- Tagline and positioning statement
- Brand story and values
- Brand personality traits

## Logo Usage
- Primary logo specifications
- Secondary/alternate logos
- Minimum size requirements
- Clear space rules
- Approved color variations
- Prohibited modifications

## Color Palette
### Primary Colors
- Color Name: HEX #XXXXXX | RGB (X, X, X) | CMYK (X, X, X, X) | Pantone XXXX

### Secondary Colors
- [Same format]

### Accent Colors
- [Same format]

## Typography
### Primary Typeface
- Font name, weights, usage

### Secondary Typeface
- Font name, weights, usage

### Type Hierarchy
- H1: Size, weight, line-height
- H2: Size, weight, line-height
- Body: Size, weight, line-height

## Voice & Tone
- Brand voice characteristics
- Tone variations by context
- Terminology glossary
- Words to use / avoid

## Imagery Guidelines
- Photography style
- Illustration style
- Icon specifications
- Graphic elements

## Legal Requirements
- Trademark usage (™, ®)
- Copyright notice format
- Required disclaimers
- Industry-specific regulations
```

## Workflow Phases

### Phase 1: Discovery and Setup

**Step 1: Guidelines Discovery**
- Agent: Brand Compliance Manager
- Action: Searches project root for brand documentation
- Output: Comprehensive catalog of all brand rules

**Step 2: Audit Scope Definition**
- Agent: Brand Compliance Manager
- Action: Identifies and categorizes all materials to audit
- Output: Organized list of materials by medium

### Phase 2: Specialist Reviews

These reviews can run in parallel for efficiency:

| Review Type | Agent | Focus Areas |
|-------------|-------|-------------|
| Visual Compliance | Brand Creative Specialist | Logo, colors, typography, imagery |
| Voice Compliance | Content Writer | Tone, messaging, terminology |
| Social Compliance | Social Media Manager | Profiles, content, engagement |
| Video Compliance | Video Marketing Specialist | Motion graphics, audio branding |
| Email Compliance | Email Marketer | Templates, rendering, mobile |
| Advertising Compliance | Paid Ads Specialist | Creative, platform rules, legal |
| Digital Compliance | SEO Specialist | Website, landing pages, meta |

### Phase 3: Consolidation and Reporting

**Step 1: Legal & Accessibility Review**
- Comprehensive legal compliance check
- WCAG accessibility audit
- Industry regulation verification

**Step 2: Findings Consolidation**
- Merge all specialist findings
- Categorize by severity
- Calculate compliance scores

**Step 3: Report Generation**
- Executive summary
- Detailed findings by category
- Compliance scores

**Step 4: Remediation Planning**
- Prioritized action items
- Timeline recommendations
- Process improvement suggestions

## Running the Workflow

### Manual Execution

```
Invoke the brand-compliance workflow for a full audit
```

### Pre-Campaign Launch

Run before any major campaign launch to ensure all materials meet brand standards.

### Scheduled Reviews

Recommended quarterly for ongoing brand health monitoring.

## Compliance Categories

### 1. Visual Identity
- Logo usage verification
- Color palette adherence
- Typography compliance
- Imagery and graphics consistency

### 2. Voice & Messaging
- Brand voice consistency
- Messaging alignment
- Terminology usage
- Content quality standards

### 3. Digital Assets
- Website compliance
- Landing page consistency
- Email template adherence
- App/product branding

### 4. Print Materials
- Pre-press requirements
- Collateral consistency
- Print-specific specifications

### 5. Video & Motion
- Animation standards
- Audio branding
- Platform requirements

### 6. Social Media
- Profile compliance
- Content consistency
- Platform-specific rules

### 7. Advertising
- Creative compliance
- Platform policies
- Performance marketing standards

### 8. Legal & Regulatory
- Trademark/copyright
- Disclosure requirements
- Industry regulations
- Claims substantiation

### 9. Accessibility
- WCAG compliance
- Content accessibility
- Interactive accessibility

## Severity Levels

| Level | Definition | Response Time |
|-------|------------|---------------|
| **Critical** | Brand damage risk, legal exposure | Immediate |
| **High** | Significant inconsistency, customer-facing | 24-48 hours |
| **Medium** | Noticeable deviation | 1 week |
| **Low** | Minor inconsistency | Next update cycle |

## Output Files

The workflow generates:

1. **brand-compliance-report.md** - Full compliance report
2. **brand-compliance-status.yaml** - Workflow status tracking
3. **remediation-plan.md** - Prioritized action items

## Best Practices

### Before the Audit
1. Ensure brand guidelines are complete and current
2. Gather all materials to be audited
3. Identify stakeholders for findings review

### During the Audit
1. Let specialists complete their reviews fully
2. Document specific examples of issues
3. Capture screenshots/evidence where possible

### After the Audit
1. Review findings with brand team
2. Prioritize remediation based on severity
3. Assign owners for each action item
4. Schedule follow-up audit

## Integration with Other Workflows

### Content Campaign Workflow
Run brand compliance check on all content before publication.

### Paid Advertising Workflow
Verify ad creative compliance before campaign launch.

### Email Sequence Workflow
Audit email templates for brand consistency.

## Troubleshooting

### No Brand Guidelines Found
If the workflow cannot find brand documentation:
1. Create a `brand-guidelines.md` file in project root
2. Document at minimum: logo rules, colors, fonts, voice
3. Re-run the workflow

### Incomplete Specialist Reviews
If a specialist agent cannot complete their review:
1. Check that relevant materials exist for that medium
2. Verify the agent has access to required checklists
3. Run that specific review step manually

### Conflicting Findings
If specialists report conflicting findings:
1. Brand Compliance Manager arbitrates
2. Refer to original brand guidelines
3. Document decision for future reference

## Customization

### Adding Custom Checks
Edit the `brand-compliance-audit-checklist.md` to add industry-specific or company-specific compliance items.

### Adjusting Severity Thresholds
Modify severity definitions in the checklist based on your organization's risk tolerance.

### Extending to New Mediums
Add new specialist agents and workflow steps for emerging channels (e.g., podcast, AR/VR).
