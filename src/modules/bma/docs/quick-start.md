# BMA Quick Start Guide

Get started with the BMad Marketing & Advertising module in 15 minutes.

## Prerequisites

- BMAD v6 installed in your project
- BMA module selected during installation
- IDE with BMAD integration (Claude Code, Cursor, Windsurf, etc.)

## Step 1: Verify Installation

After BMAD installation, verify BMA is available:

```
{your-project}/
└── .bmad/
    └── bma/
        ├── agents/
        ├── workflows/
        ├── teams/
        ├── templates/
        ├── checklists/
        └── data/
```

## Step 2: Load Your First Agent

In your IDE, load a marketing agent. The method depends on your IDE:

**Claude Code:**
```
/bmad:bma:agents:content-writer
```

**Cursor/Windsurf:**
Load the agent file or use the configured command.

## Step 3: See Available Commands

Once the agent is loaded, type:
```
*help
```

You'll see the agent's menu of available workflows and commands.

## Step 4: Run Your First Workflow

Try creating a blog post:
```
*create-blog-post
```

The agent will guide you through the workflow interactively.

## Step 5: Collaborate with the Team

Bring in other marketing experts:
```
*party-mode
```

This activates multi-agent collaboration for complex marketing challenges.

## Common First Tasks

### Create Blog Content
1. Load `content-writer`
2. Run `*create-blog-post`
3. Follow the prompts for topic, audience, and keywords

### Plan Email Campaign
1. Load `email-marketer`
2. Run `*create-email-campaign`
3. Define goals, audience, and sequence

### Launch Paid Ads
1. Load `paid-ads-specialist`
2. Run `*google-ads-campaign`
3. Define objectives, budget, and targeting

### Audit SEO
1. Load `seo-specialist`
2. Run `*on-page-audit`
3. Provide URL or content to analyze

## Available Agents

| Agent | Load Command | Primary Use |
|-------|--------------|-------------|
| Content Writer | `content-writer` | Blog posts, sales copy |
| Email Marketer | `email-marketer` | Email campaigns |
| Social Media Manager | `social-media-manager` | Social content |
| Paid Ads Specialist | `paid-ads-specialist` | PPC campaigns |
| SEO Specialist | `seo-specialist` | Search optimization |
| Video Marketing | `video-marketing-specialist` | Video content |
| Outreach Specialist | `outreach-specialist` | Partnerships |
| Analytics & Automation | `analytics-automation-specialist` | Data & automation |
| E-commerce Specialist | `ecommerce-specialist` | Conversion optimization |
| Brand & Creative | `brand-creative-specialist` | Brand strategy |

## Next Steps

- Explore the [Agents Guide](./agents-guide.md) for detailed agent capabilities
- Review [Templates](../templates/) for ready-to-use marketing assets
- Check [Checklists](../checklists/) for quality validation
- Read the [Knowledge Base](../data/bmad-kb.md) for marketing best practices

## Getting Help

- Type `*help` with any agent for available commands
- Join [Discord](https://discord.gg/gk8jAdXWmj) for community support
