---
name: frontend
description: Frontend development skill - React, Vue, performance, accessibility
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [build, debug, optimize, style, test] }
    framework: { type: string, enum: [react, vue, angular, svelte] }
  required: [task]

output_schema:
  type: object
  properties:
    code: { type: string }
    styles: { type: string }
    best_practices: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 30000
---

# Frontend Development Skill

## PURPOSE
Modern frontend development with React, Vue, and performance optimization.

## CORE COMPETENCIES
```
Frameworks:
├── React 19 (Server Components)
├── Vue 3 (Composition API)
├── Angular 18 (Signals)
└── Next.js / Nuxt

Styling:
├── Tailwind CSS
├── CSS-in-JS
├── CSS Grid/Flexbox
└── Responsive design

Performance:
├── Core Web Vitals
├── Code splitting
├── Lazy loading
└── Image optimization
```

## CODE PATTERNS

### React Component
```tsx
import { useState, useCallback, memo } from 'react';

interface Props {
  items: Item[];
  onSelect: (id: string) => void;
}

export const ItemList = memo(function ItemList({ items, onSelect }: Props) {
  const [filter, setFilter] = useState('');

  const filteredItems = useMemo(
    () => items.filter(item => item.name.includes(filter)),
    [items, filter]
  );

  const handleSelect = useCallback((id: string) => {
    onSelect(id);
  }, [onSelect]);

  return (
    <div className="space-y-4">
      <input
        type="text"
        value={filter}
        onChange={(e) => setFilter(e.target.value)}
        className="w-full px-4 py-2 border rounded"
        aria-label="Filter items"
      />
      <ul role="list">
        {filteredItems.map(item => (
          <li key={item.id}>
            <button onClick={() => handleSelect(item.id)}>
              {item.name}
            </button>
          </li>
        ))}
      </ul>
    </div>
  );
});
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| Slow render | Too many re-renders | useMemo, useCallback, memo |
| Memory leak | Uncleared effects | Cleanup in useEffect |
| Hydration mismatch | Server/client diff | Ensure consistent render |

## ACCESSIBILITY
```
[ ] Semantic HTML
[ ] ARIA labels
[ ] Keyboard navigation
[ ] Color contrast
[ ] Focus management
```
