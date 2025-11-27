# BMA - BMad Marketing & Advertising Module

> Powered by BMAD™ Core v6

Comprehensive AI-powered marketing and advertising framework providing specialized agents for content creation, email marketing, social media, paid advertising, SEO, analytics, e-commerce, branding, and immersive experiences.

---

## 📦 Package Contents

- **11 Specialized Agents** - Expert AI personas for every marketing discipline
- **4 Multi-Agent Workflows** - End-to-end processes from strategy to execution
- **24 Quality Checklists** - Validation for content, email, ads, SEO, and more
- **25 Templates** - Ready-to-use marketing asset templates
- **4 Data Files** - Knowledge base and frameworks reference

---

## 🤖 Agent Team (11 Agents)

| Agent | Icon | Description |
|-------|------|-------------|
| **Content Writer** | ✍️ | Blog posts, sales copy, landing pages, SEO content |
| **Video Marketing Specialist** | 🎬 | YouTube ads, video scripts, content strategy |
| **Email Marketer** | 📧 | Email campaigns, sequences, automation, deliverability |
| **Social Media Manager** | 📱 | Twitter threads, Instagram, social strategy, community |
| **Paid Ads Specialist** | 💰 | Facebook ads, Google Ads, PPC, display advertising |
| **Outreach Specialist** | 🤝 | Cold DMs, influencer partnerships, creator outreach |
| **SEO Specialist** | 🔍 | On-page, off-page, technical SEO optimization |
| **Analytics & Automation** | 📊 | Analytics, reporting, automation, CRM, lead scoring |
| **E-commerce Specialist** | 🛒 | Product pages, cart optimization, conversion funnels |
| **Brand & Creative** | 🎨 | Brand identity, visual design, AR/VR experiences |
| **Brand Compliance Manager** | ✅ | Multi-medium brand compliance audits, guideline enforcement |

---

## 🔄 Workflows

1. **Content Campaign** - End-to-end content marketing workflow
2. **Email Sequence** - Automated email campaign creation
3. **Paid Advertising** - PPC and paid social campaign launch
4. **Brand Compliance** - Multi-agent brand compliance audit across all mediums

*Additional workflows (social-media-launch, seo-optimization, influencer-outreach, lead-generation, ecommerce-optimization) can be added using the same pattern.*

---

## 🏗️ Module Structure (v6)

```
bma/
├── _module-installer/
│   └── install-config.yaml    # Module installation configuration
├── agents/                     # 11 specialized agent definitions (.agent.yaml)
├── workflows/                  # Multi-agent workflow definitions
│   ├── content-campaign/
│   ├── email-sequence/
│   ├── paid-advertising/
│   └── brand-compliance/
├── teams/                      # Agent team bundles
│   ├── team-marketing-full.yaml
│   ├── team-content-growth.yaml
│   ├── team-paid-acquisition.yaml
│   └── default-party.csv
├── templates/                  # 25 YAML-driven templates
├── checklists/                 # 24 quality assurance checklists
├── data/                       # Reference data and frameworks
├── docs/                       # Documentation
└── README.md
```

---

## 🚀 Quick Start

### Installation

```bash
# Install BMAD with BMA module
npx bmad-method@alpha install

# Select BMA module during installation
```

### Usage

```bash
# Load any marketing agent in your IDE, then:
*help                    # See available commands
*create-blog-post        # Start content workflow
*create-email-campaign   # Start email workflow
*party-mode              # Collaborate with all agents
```

---

## 📋 Templates (25)

### Content & Copy
- `blog-post-tmpl.yaml` - SEO-optimized blog post
- `sales-copy-tmpl.yaml` - Conversion-focused sales copy
- `landing-page-tmpl.yaml` - High-converting landing pages

### Email Marketing
- `email-campaign-tmpl.yaml` - Email campaign planning
- `drip-sequence-tmpl.yaml` - Automated sequences
- `cart-recovery-tmpl.yaml` - Cart abandonment emails

### Social Media
- `twitter-thread-tmpl.yaml` - Engaging Twitter threads
- `instagram-story-tmpl.yaml` - Instagram story content
- `content-calendar-tmpl.yaml` - Social content planning

### Paid Advertising
- `facebook-ad-tmpl.yaml` - Facebook/Meta ad copy
- `google-ads-tmpl.yaml` - Google Ads campaigns
- `youtube-ad-tmpl.yaml` - YouTube ad scripts
- `campaign-structure-tmpl.yaml` - Campaign organization

### SEO & Analytics
- `seo-audit-tmpl.yaml` - SEO audit framework
- `keyword-map-tmpl.yaml` - Keyword research mapping
- `analytics-report-tmpl.yaml` - Performance reporting

### Outreach & Partnerships
- `cold-dm-tmpl.yaml` - Cold outreach messages
- `influencer-brief-tmpl.yaml` - Influencer content briefs
- `partnership-proposal-tmpl.yaml` - Partnership proposals

### Brand & E-commerce
- `brand-guidelines-tmpl.yaml` - Brand guidelines
- `design-brief-tmpl.yaml` - Creative briefs
- `product-page-tmpl.yaml` - Product page optimization
- `campaign-brief-tmpl.yaml` - Campaign planning

---

## ✅ Checklists (24)

### Content Quality
- `content-quality-checklist.md`
- `seo-content-checklist.md`
- `conversion-copy-checklist.md`

### Email Marketing
- `email-quality-checklist.md`
- `deliverability-checklist.md`

### Social Media
- `social-content-checklist.md`
- `engagement-checklist.md`

### Paid Advertising
- `paid-ads-checklist.md`
- `campaign-launch-checklist.md`

### SEO
- `on-page-seo-checklist.md`
- `technical-seo-checklist.md`
- `link-building-checklist.md`

### E-commerce
- `ecommerce-audit-checklist.md`
- `ecommerce-product-page-checklist.md`
- `product-page-checklist.md`
- `conversion-optimization-checklist.md`

### Brand & Creative
- `brand-consistency-checklist.md`
- `creative-review-checklist.md`

### Outreach
- `outreach-quality-checklist.md`
- `influencer-vetting-checklist.md`

### Analytics & Automation
- `analytics-audit-checklist.md`
- `automation-checklist.md`

### Video
- `video-ad-checklist.md`
- `youtube-optimization-checklist.md`

---

## 📊 Data Files

- `bmad-kb.md` - Marketing & Advertising knowledge base
- `content-frameworks.md` - Content strategy frameworks
- `headline-formulas.md` - Proven headline patterns
- `marketing-frameworks.md` - Marketing strategy frameworks

---

## 🎯 Use Cases

- **Content Marketing**: Blog posts, articles, SEO content
- **Email Campaigns**: Newsletters, drip sequences, automation
- **Social Media**: Platform-specific content, engagement, growth
- **Paid Advertising**: PPC, display, social ads, retargeting
- **SEO**: Technical optimization, link building, local SEO
- **Lead Generation**: Capture, scoring, nurturing, conversion
- **Brand Building**: Awareness, positioning, storytelling
- **Analytics**: Tracking, reporting, optimization
- **Brand Compliance**: Multi-medium audits, guideline enforcement

---

## ✅ Brand Compliance Setup

The **Brand Compliance Manager** agent automatically discovers brand guidelines from MD files in your project root. Place your brand documentation using any of these naming patterns:

### English
- `*brand*.md` - Brand guidelines, brand book
- `*style*.md` - Style guides
- `*guideline*.md` - General guidelines
- `*identity*.md` - Visual identity
- `*compliance*.md` - Compliance requirements
- `*standards*.md` - Brand standards

### Français
- `*marque*.md` - Directives de marque
- `*charte*.md` - Charte graphique
- `*graphique*.md` - Identité graphique
- `*identite*.md` - Identité visuelle
- `*conformite*.md` - Exigences de conformité
- `*normes*.md` - Normes de marque

### Language-Agnostic
- `README.md` - Project readme (may contain brand info)
- `*logo*.md` - Logo usage rules
- `*color*.md` / `*colour*.md` - Color palette specifications
- `*font*.md` - Font/typography rules
- `*typo*.md` - Typography guidelines

### Example Brand Guidelines File

Create a `brand-guidelines.md` (or `charte-graphique.md` for French) in your project root:

```markdown
# Brand Guidelines

## Logo
- Primary logo: [specifications]
- Minimum size: 24px height
- Clear space: 1x logo height

## Colors
- Primary: #1A73E8 (Blue)
- Secondary: #34A853 (Green)
- Accent: #FBBC04 (Yellow)

## Typography
- Headlines: Inter Bold
- Body: Inter Regular
- Code: JetBrains Mono

## Voice & Tone
- Professional but approachable
- Clear and concise
- Action-oriented
```

The compliance workflow will automatically load these files and audit all marketing materials against them

---

## 🔧 Customization

Customize agents without modifying core files:

```yaml
# {bmad_folder}/_cfg/agents/bma-content-writer.customize.yaml
agent:
  metadata:
    name: 'Your Custom Name'

memories:
  - 'Our brand voice is casual and friendly'
  - 'We target B2B SaaS companies'

critical_actions:
  - 'Always check brand guidelines before writing'
```

After editing, rebuild:
```bash
npx bmad-method build bma-content-writer
```

---

## 📖 Migration from V4

This module was migrated from the v4 `marketing-advertising` expansion pack. Key changes:

| V4 Pattern | V6 Pattern |
|------------|------------|
| `.md` agent files with YAML block | `.agent.yaml` structured files |
| `config.yaml` with `slashPrefix` | `_module-installer/install-config.yaml` with `code` |
| Flat workflow YAML | Workflow folders with `workflow.yaml` + `instructions.md` |
| `agent-teams/` folder | `teams/` with party CSV |

---

## 🤝 Community

- **[Discord](https://discord.gg/gk8jAdXWmj)** - Get help, share feedback
- **[GitHub Issues](https://github.com/bmad-code-org/BMAD-METHOD/issues)** - Report bugs or request features

---

*Part of the BMAD Method ecosystem*
