---
name: backend
description: Backend development skill - APIs, databases, authentication, caching
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [api, database, auth, cache, optimize] }
    framework: { type: string }
  required: [task]

output_schema:
  type: object
  properties:
    code: { type: string }
    schema: { type: string }
    best_practices: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 30000
---

# Backend Development Skill

## PURPOSE
API development, database design, and server-side architecture.

## CORE COMPETENCIES
```
APIs:
├── REST design
├── GraphQL
├── gRPC
└── WebSocket

Databases:
├── PostgreSQL
├── MongoDB
├── Redis
└── Query optimization

Security:
├── Authentication (JWT, OAuth)
├── Authorization (RBAC)
├── Input validation
└── Rate limiting
```

## CODE PATTERNS

### Express/Node API
```typescript
import express from 'express';
import { z } from 'zod';

const userSchema = z.object({
  email: z.string().email(),
  name: z.string().min(1).max(100),
});

app.post('/users', async (req, res) => {
  try {
    const data = userSchema.parse(req.body);
    const user = await db.user.create({ data });
    res.status(201).json(user);
  } catch (error) {
    if (error instanceof z.ZodError) {
      return res.status(400).json({ errors: error.errors });
    }
    res.status(500).json({ error: 'Internal server error' });
  }
});
```

### FastAPI
```python
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel, EmailStr

class UserCreate(BaseModel):
    email: EmailStr
    name: str

@app.post("/users", status_code=201)
async def create_user(user: UserCreate):
    try:
        return await db.create_user(user.dict())
    except DuplicateError:
        raise HTTPException(400, "Email already exists")
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| N+1 queries | Lazy loading | Eager loading, DataLoader |
| Slow response | No caching | Add Redis cache |
| Connection exhaustion | No pooling | Connection pool |

## BEST PRACTICES
```
1. Validate all inputs
2. Use connection pooling
3. Implement proper error handling
4. Add request/response logging
5. Use database transactions
```
