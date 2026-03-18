---
name: "design"
displayName: "Design"
description: "Design critique, UX writing, accessibility audits, design system management, research synthesis, and developer handoff. Works with Figma and other tools or standalone."
keywords: ["design critique", "critique", "review design", "design feedback", "design system", "audit components", "tokens", "ux copy", "microcopy", "error message", "empty state", "accessibility", "a11y", "WCAG", "contrast", "keyboard navigation", "research synthesis", "user research", "interview", "usability test", "handoff", "dev handoff", "spec", "design spec", "figma"]
author: "reefwn"
---

# Onboarding

## Step 1: Check environment

Look for existing design context:
- Design system documentation or component libraries
- Brand voice or content style guides
- Existing research repositories or findings
- Figma files or design tool links

## Step 2: Gather team context

Ask the user:
```
To personalize your design workflows, I'd like to know:
1. Your name and role
2. Your team name and company
3. Your design tools (Figma, Sketch, etc.)
4. Your tech stack for handoff (React, iOS, Android, etc.)
5. Your brand voice (formal, friendly, playful, etc.)
```

Store responses for use across all workflows.

## Step 3: Report readiness

```
Design power ready. Available workflows:
- /critique — Structured design feedback
- /design-system — Audit, document, or extend your design system
- /handoff — Developer handoff specs
- /ux-copy — Write or review UX copy
- /accessibility — WCAG 2.1 AA accessibility audit
- /research-synthesis — Synthesize user research into insights

Skills loaded automatically when relevant:
design-critique, design-system-management, ux-writing, accessibility-review, user-research, design-handoff
```

# Connectors

This power uses tool categories as placeholders. Any MCP server in that category works.

| Category | Placeholder | Examples |
|----------|-------------|----------|
| Chat | ~~chat | Slack, Microsoft Teams |
| Design tool | ~~design tool | Figma, Sketch, Adobe XD, Framer |
| Knowledge base | ~~knowledge base | Notion, Confluence, Guru, Coda |
| Project tracker | ~~project tracker | Linear, Asana, Jira, Shortcut, ClickUp |
| User feedback | ~~user feedback | Intercom, Productboard, Canny, UserVoice, Dovetail |
| Product analytics | ~~product analytics | Amplitude, Mixpanel, Heap, FullStory |

# When to Load Steering Files

- Running `/critique` or asking for design feedback → `critique.md`
- Running `/design-system` or asking about components, tokens, patterns → `design-system.md`
- Running `/handoff` or preparing specs for developers → `handoff.md`
- Running `/ux-copy` or writing microcopy, error messages, CTAs → `ux-copy.md`
- Running `/accessibility` or auditing for WCAG compliance → `accessibility.md`
- Running `/research-synthesis` or synthesizing interviews, surveys, tests → `research-synthesis.md`
- Discussing design evaluation, usability, or visual hierarchy → `design-critique.md`
- Managing design tokens, component libraries, or pattern docs → `design-system-management.md`
- Writing UX copy, microcopy, or content for interfaces → `ux-writing.md`
- Reviewing accessibility, contrast, keyboard nav, screen readers → `accessibility-review.md`
- Planning or conducting user research studies → `user-research.md`
- Creating developer handoff documentation → `design-handoff.md`

# Credits

Ported from [Anthropic's Claude Cowork plugins](https://github.com/anthropics/knowledge-work-plugins) by [@reefwn](https://github.com/reefwn).
