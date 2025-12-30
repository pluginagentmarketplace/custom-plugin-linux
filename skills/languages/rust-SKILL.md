---
name: rust
description: Rust development skill - Memory safety, systems programming, async Rust
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [code, debug, explain, optimize, review] }
    context: { type: string, enum: [systems, web, cli, embedded] }
  required: [task]

output_schema:
  type: object
  properties:
    solution: { type: string }
    safety_notes: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 30000
---

# Rust Skill

## PURPOSE
Systems programming with memory safety and fearless concurrency.

## CORE COMPETENCIES
```
Ownership Model:
├── Ownership rules
├── Borrowing (&, &mut)
├── Lifetimes
└── Move semantics

Error Handling:
├── Result<T, E>
├── Option<T>
├── ? operator
└── thiserror/anyhow

Async Rust:
├── async/await
├── Tokio runtime
└── Channels (mpsc)
```

## CODE PATTERNS

### Error Handling
```rust
use thiserror::Error;

#[derive(Error, Debug)]
pub enum AppError {
    #[error("Database error: {0}")]
    Database(#[from] sqlx::Error),
    #[error("Not found")]
    NotFound,
}
```

### Retry Pattern
```rust
async fn with_retry<T, F, Fut>(f: F, attempts: u32) -> Result<T>
where
    F: Fn() -> Fut,
    Fut: Future<Output = Result<T>>,
{
    for _ in 0..attempts {
        if let Ok(r) = f().await { return Ok(r); }
    }
    f().await
}
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| Borrow checker | Lifetime conflict | Use Rc/Arc |
| Deadlock | Lock ordering | Review lock order |

## TESTING
```rust
#[cfg(test)]
mod tests {
    #[test]
    fn test_function() {
        assert_eq!(fn("input"), "expected");
    }

    #[tokio::test]
    async fn test_async() {
        assert!(async_fn().await.is_ok());
    }
}
```
