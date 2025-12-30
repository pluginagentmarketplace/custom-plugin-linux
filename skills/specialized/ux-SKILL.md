---
name: ux
description: UX/UI design skill - User research, prototyping, design systems, accessibility
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [research, design, prototype, test, audit] }
    focus: { type: string, enum: [mobile, web, desktop, cross_platform] }
  required: [task]

output_schema:
  type: object
  properties:
    wireframes: { type: array }
    recommendations: { type: array }
    accessibility_report: { type: object }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 30000
---

# UX/UI Design Skill

## PURPOSE
User experience design, interface design, and usability optimization.

## CORE COMPETENCIES
```
User Research:
├── User interviews
├── Surveys & analytics
├── Persona development
├── Journey mapping
└── Competitive analysis

Design:
├── Wireframing
├── Visual design
├── Interaction design
├── Design systems
└── Responsive design

Prototyping:
├── Figma
├── Sketch
├── Adobe XD
├── Framer
└── Principle

Testing:
├── Usability testing
├── A/B testing
├── Heatmaps
├── Session recording
└── Accessibility audits
```

## DESIGN PATTERNS

### Design System Structure
```
Design System:
├── Foundations
│   ├── Colors (semantic naming)
│   ├── Typography (scale, hierarchy)
│   ├── Spacing (8px grid)
│   ├── Shadows & elevation
│   └── Icons
│
├── Components
│   ├── Atoms (buttons, inputs, labels)
│   ├── Molecules (form fields, cards)
│   ├── Organisms (navigation, modals)
│   └── Templates (page layouts)
│
└── Patterns
    ├── Navigation
    ├── Forms
    ├── Data display
    └── Feedback
```

### Accessibility Checklist (WCAG 2.2)
```
Perceivable:
├── [ ] Alt text for images
├── [ ] Captions for video
├── [ ] Color contrast 4.5:1
├── [ ] Resize up to 200%
└── [ ] No color-only meaning

Operable:
├── [ ] Keyboard accessible
├── [ ] Focus indicators
├── [ ] Skip navigation
├── [ ] No time limits
└── [ ] No seizure triggers

Understandable:
├── [ ] Clear language
├── [ ] Consistent navigation
├── [ ] Error identification
├── [ ] Labels for inputs
└── [ ] Predictable behavior

Robust:
├── [ ] Valid HTML
├── [ ] ARIA when needed
├── [ ] Works with assistive tech
└── [ ] Cross-browser tested
```

### Component Specification
```yaml
# Button Component Spec
button:
  variants:
    - primary: High-emphasis actions
    - secondary: Medium-emphasis
    - tertiary: Low-emphasis
    - danger: Destructive actions

  sizes:
    - small: 32px height
    - medium: 40px height (default)
    - large: 48px height

  states:
    - default
    - hover
    - focus (visible ring)
    - active (pressed)
    - disabled (0.5 opacity)
    - loading (spinner)

  accessibility:
    - role: button
    - aria-disabled: when disabled
    - aria-busy: when loading
    - focus: visible outline
```

## UX HEURISTICS (Nielsen)
```
1. Visibility of system status
2. Match real world
3. User control & freedom
4. Consistency & standards
5. Error prevention
6. Recognition over recall
7. Flexibility & efficiency
8. Aesthetic & minimal
9. Help users with errors
10. Help & documentation
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| Low conversion | Friction in flow | Simplify steps |
| High bounce | Poor first impression | Improve hero/CTA |
| User confusion | Unclear navigation | Card sorting, testing |
| Accessibility fail | Missing semantics | ARIA, proper HTML |
