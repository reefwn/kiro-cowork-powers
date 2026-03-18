# /handoff

Generate comprehensive developer handoff documentation from a design.

## Usage

```
/handoff
```

Share a Figma link, screenshot, or describe the design. Specify the tech stack for relevant implementation notes.

## What to Include

### Visual Specifications
- Exact measurements (padding, margins, widths)
- Design token references (colors, typography, spacing)
- Responsive breakpoints and behavior
- Component variants and states

### Interaction Specifications
- Click/tap behavior, hover states
- Transitions and animations (duration, easing)
- Gesture support (swipe, pinch, long-press)

### Content Specifications
- Character limits, truncation behavior
- Empty states, loading states, error states

### Edge Cases
- Minimum/maximum content
- International text (longer strings)
- Slow connections, missing data

### Accessibility
- Focus order, ARIA labels and roles
- Keyboard interactions, screen reader announcements

## Principles

1. **Don't assume** — If it's not specified, the developer will guess
2. **Use tokens, not values** — Reference `spacing-md` not `16px`
3. **Show all states** — Default, hover, active, disabled, loading, error, empty
4. **Describe the why** — Context helps developers make good judgment calls

## Output

```markdown
## Handoff Spec: [Feature/Screen Name]

### Overview
[What this screen/feature does, user context]

### Design Tokens Used
| Token | Value | Usage |
|-------|-------|-------|
| `color-primary` | #[hex] | CTA buttons, links |
| `spacing-md` | [X]px | Between sections |

### Components
| Component | Variant | Props | Notes |
|-----------|---------|-------|-------|

### States and Interactions
| Element | State | Behavior |
|---------|-------|----------|
| [CTA Button] | Hover | [Background darken 10%] |
| [CTA Button] | Loading | [Spinner, disabled] |

### Responsive Behavior
| Breakpoint | Changes |
|------------|---------|
| Desktop (>1024px) | [Default layout] |
| Tablet (768-1024px) | [What changes] |
| Mobile (<768px) | [What changes] |

### Edge Cases
- **Empty state**: [What to show when no data]
- **Long text**: [Truncation rules]
- **Loading**: [Skeleton or spinner]
- **Error**: [Error state appearance]

### Animation / Motion
| Element | Trigger | Animation | Duration | Easing |
|---------|---------|-----------|----------|--------|

### Accessibility Notes
- [Focus order]
- [ARIA labels needed]
- [Keyboard interactions]
```

## If Connectors Available

If **~~design tool** is connected:
- Pull exact measurements, tokens, and component specs from Figma
- Export assets and generate a complete spec sheet

If **~~project tracker** is connected:
- Link the handoff to the implementation ticket
- Create sub-tasks for each section of the spec
