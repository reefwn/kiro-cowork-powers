# Accessibility Review

Audit designs and code for WCAG 2.1 AA compliance.

## When This Applies

Loaded when reviewing designs or code for accessibility, color contrast, keyboard navigation, screen reader support, or touch target sizing.

## Key Criteria

- **Contrast**: >= 4.5:1 normal text, >= 3:1 large text and UI components
- **Keyboard**: All functionality available, logical focus order, visible focus indicator
- **Touch targets**: >= 44x44 CSS pixels
- **Semantics**: Proper ARIA roles, labels, and landmarks
- **Predictability**: No unexpected changes on focus, clear error identification

## Testing Approach

1. Automated scan (catches ~30%)
2. Keyboard-only navigation
3. Screen reader testing
4. Color contrast verification
5. Zoom to 200%
