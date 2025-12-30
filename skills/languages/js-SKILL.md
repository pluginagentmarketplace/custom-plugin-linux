---
name: javascript
description: JavaScript/TypeScript development skill - Modern ES2024+, Node.js, async patterns, and frontend frameworks
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [code, debug, explain, optimize, review] }
    context: { type: string }
    code_snippet: { type: string }
  required: [task]

output_schema:
  type: object
  properties:
    solution: { type: string }
    explanation: { type: string }
    best_practices: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential
  initial_delay_ms: 1000

timeout_ms: 30000
---

# JavaScript/TypeScript Skill

## PURPOSE
Atomic skill for JavaScript and TypeScript development tasks.

## CORE COMPETENCIES
```
ES2024+ Features:
├── Optional chaining (?.)
├── Nullish coalescing (??)
├── Top-level await
├── Array methods (toSorted, toReversed)
└── Temporal API (coming)

TypeScript:
├── Type inference
├── Generics
├── Utility types (Partial, Pick, Omit)
├── Discriminated unions
└── Satisfies operator

Async Patterns:
├── Promises
├── async/await
├── Error handling
├── Concurrent execution
└── Stream processing
```

## CODE PATTERNS

### Error Handling
```typescript
// Production-grade error handling
async function fetchWithRetry<T>(
  fn: () => Promise<T>,
  retries = 3,
  delay = 1000
): Promise<T> {
  try {
    return await fn();
  } catch (error) {
    if (retries === 0) throw error;
    await new Promise(r => setTimeout(r, delay));
    return fetchWithRetry(fn, retries - 1, delay * 2);
  }
}
```

### Type-Safe API Response
```typescript
interface ApiResponse<T> {
  data: T;
  error?: { code: string; message: string };
  metadata: { timestamp: number; requestId: string };
}

function handleResponse<T>(response: ApiResponse<T>): T {
  if (response.error) {
    throw new Error(`${response.error.code}: ${response.error.message}`);
  }
  return response.data;
}
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| `undefined is not a function` | Missing method | Check object shape, use optional chaining |
| Memory leak | Uncleared listeners | Remove event listeners, use WeakMap |
| Callback hell | Nested callbacks | Convert to async/await |
| Type errors | Incorrect inference | Add explicit type annotations |

## TESTING TEMPLATE
```typescript
import { describe, it, expect, vi } from 'vitest';

describe('functionName', () => {
  it('should handle normal input', () => {
    expect(fn('input')).toBe('expected');
  });

  it('should throw on invalid input', () => {
    expect(() => fn(null)).toThrow();
  });

  it('should handle async operations', async () => {
    const result = await asyncFn();
    expect(result).toBeDefined();
  });
});
```

## OBSERVABILITY
```typescript
// Logging wrapper
const withLogging = <T extends (...args: any[]) => any>(fn: T, name: string) =>
  (...args: Parameters<T>): ReturnType<T> => {
    console.log(`[${name}] Called with:`, args);
    const result = fn(...args);
    console.log(`[${name}] Returned:`, result);
    return result;
  };
```
