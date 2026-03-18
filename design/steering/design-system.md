# /design-system

Audit, document, or extend your design system — components, tokens, patterns.

## Usage

```
/design-system audit          # Full system audit
/design-system document [component]  # Document a component
/design-system extend [pattern]      # Design a new component or pattern
```

## Components of a Design System

### Design Tokens
Atomic values: colors (brand, semantic, neutral), typography (scale, weights, line heights), spacing, borders, shadows, motion.

### Components
Reusable UI elements with defined variants, states (default, hover, active, disabled, loading, error), sizes, behavior, and accessibility.

### Patterns
Common UI solutions combining components: forms, navigation, data display, feedback.

## Principles

1. **Consistency over creativity** — The system exists so teams don't reinvent the wheel
2. **Flexibility within constraints** — Components should be composable, not rigid
3. **Document everything** — If it's not documented, it doesn't exist
4. **Version and migrate** — Breaking changes need migration paths

## Output — Audit

```markdown
## Design System Audit

### Summary
**Components reviewed:** [X] | **Issues found:** [X] | **Score:** [X/100]

### Naming Consistency
| Issue | Components | Recommendation |
|-------|------------|----------------|
| [Inconsistent naming] | [List] | [Standard to adopt] |

### Token Coverage
| Category | Defined | Hardcoded Values Found |
|----------|---------|----------------------|
| Colors | [X] | [X] instances of hardcoded hex |
| Spacing | [X] | [X] instances of arbitrary values |
| Typography | [X] | [X] instances of custom fonts/sizes |

### Component Completeness
| Component | States | Variants | Docs | Score |
|-----------|--------|----------|------|-------|
| Button | ✅ | ✅ | ⚠️ | 8/10 |

### Priority Actions
1. [Most impactful improvement]
2. [Second priority]
```

## Output — Document

```markdown
## Component: [Name]

### Description
[What this component is and when to use it]

### Variants
| Variant | Use When |
|---------|----------|
| [Primary] | [Main actions] |

### Props / Properties
| Property | Type | Default | Description |
|----------|------|---------|-------------|

### States
| State | Visual | Behavior |
|-------|--------|----------|
| Default | [description] | — |
| Hover | [description] | [interaction] |
| Disabled | [description] | Non-interactive |

### Accessibility
- **Role**: [ARIA role]
- **Keyboard**: [Tab, Enter, Escape behavior]
- **Screen reader**: [Announced as...]

### Do's and Don'ts
| ✅ Do | ❌ Don't |
|------|---------|
```

## Output — Extend

```markdown
## New Component: [Name]

### Problem
[What user need or gap this component addresses]

### Existing Patterns
| Related Component | Similarity | Why It's Not Enough |
|-------------------|-----------|---------------------|

### Proposed Design
#### API / Props
| Property | Type | Default | Description |
|----------|------|---------|-------------|

#### Tokens Used
- Colors: [Which tokens]
- Spacing: [Which tokens]
- Typography: [Which tokens]

### Accessibility
- **Role**: [ARIA role]
- **Keyboard**: [Expected interactions]
- **Screen reader**: [Announced as...]
```

## If Connectors Available

If **~~design tool** is connected:
- Audit components directly in Figma — check naming, variants, and token usage
- Pull component properties and layer structure for documentation

If **~~knowledge base** is connected:
- Search for existing component documentation and usage guidelines
- Publish updated documentation to your wiki
