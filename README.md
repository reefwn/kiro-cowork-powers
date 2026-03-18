# cowork-powers

Kiro Powers translated from [Claude Cowork plugins](https://github.com/anthropics/knowledge-work-plugins). Each subdirectory is a standalone Kiro Power that can be installed via **Powers panel → Add power from GitHub**.

## Available Powers

| Power | Description | Status | Source |
|-------|-------------|--------|--------|
| [bio-research](./bio-research) | Preclinical research tools and databases for life sciences R&D | ✅ | [Original](https://claude.com/plugins/bio-research) |
| [customer-support](./customer-support) | Ticket triage, response drafting, and knowledge base | ✅ | [Original](https://claude.com/plugins/customer-support) |
| [data](./data) | SQL, dataset exploration, visualizations, and dashboards | ✅ | [Original](https://claude.com/plugins/data) |
| [design](./design) | Design critique, UX writing, accessibility audits, and dev handoff | ✅ | [Original](https://claude.com/plugins/design) |
| [engineering](./engineering) | Standups, code review, architecture decisions, and incident response | ✅ | [Original](https://claude.com/plugins/engineering) |
| [enterprise-search](./enterprise-search) | Search across company tools — email, chat, documents, wikis | ✅ | [Original](https://claude.com/plugins/enterprise-search) |
| [finance](./finance) | Journal entries, reconciliation, and financial statements | ✅ | [Original](https://claude.com/plugins/finance) |
| [human-resources](./human-resources) | Recruiting, onboarding, performance reviews, and policy guidance | ✅ | [Original](https://claude.com/plugins/human-resources) |
| [legal](./legal) | Contract review, NDA triage, and compliance workflows | ✅ | [Original](https://claude.com/plugins/legal) |
| [marketing](./marketing) | Content creation, campaign planning, and performance analysis | ✅ | [Original](https://claude.com/plugins/marketing) |
| [operations](./operations) | Vendor management, process docs, change management, and compliance | ✅ | [Original](https://claude.com/plugins/operations) |
| [product-management](./product-management) | Feature specs, roadmaps, and user research synthesis | ✅ | [Original](https://claude.com/plugins/product-management) |
| [productivity](./productivity) | Task management, workplace memory, and daily sync | ✅ | [Original](https://claude.com/plugins/productivity) |
| [sales](./sales) | Prospect, craft outreach, and build deal strategy | ✅ | [Original](https://claude.com/plugins/sales) |

## Installation

Each power is installed independently. In Kiro IDE:

1. Open the **Powers** panel
2. Click **Add power from GitHub**
3. Enter the URL pointing to the specific power subdirectory:
   ```
   https://github.com/reefwn/cowork-powers/tree/main/<power>
   ```
4. The power registers automatically with its MCP servers and steering files

## How It Works

Each power follows the [Kiro Power format](https://kiro.dev/docs/powers/create/):

```
<power-name>/
├── POWER.md          # Metadata, onboarding, steering mappings
├── mcp.json          # MCP server configuration (connectors)
└── steering/         # Workflow-specific guidance files
```

- **POWER.md** — Defines keywords for activation, onboarding steps, and which steering files to load
- **mcp.json** — Pre-configures MCP servers (Slack, Jira, Notion, etc.) for the power's domain
- **steering/** — Detailed workflow instructions loaded on-demand based on context

## Credits

Based on [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) (MIT License).
