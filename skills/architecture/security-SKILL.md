---
name: security
description: Security skill - OWASP, authentication, encryption, compliance
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [audit, implement, review, compliance, incident] }
    domain: { type: string, enum: [web, api, infrastructure, data] }
  required: [task]

output_schema:
  type: object
  properties:
    findings: { type: array }
    recommendations: { type: array }
    code: { type: string }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 60000
---

# Security Skill

## PURPOSE
Application security, authentication, and compliance.

## CORE COMPETENCIES
```
OWASP Top 10:
├── Broken Access Control
├── Cryptographic Failures
├── Injection
├── Insecure Design
├── Security Misconfiguration
├── Vulnerable Components
├── Auth Failures
├── Data Integrity
├── Logging Failures
└── SSRF

Authentication:
├── OAuth 2.1 / OIDC
├── JWT best practices
├── Passkeys / WebAuthn
├── MFA
└── Session management

Encryption:
├── TLS 1.3
├── AES-256 at rest
├── Key management
└── Hashing (Argon2, bcrypt)
```

## CODE PATTERNS

### Input Validation
```typescript
import { z } from 'zod';

const userInput = z.object({
  email: z.string().email(),
  password: z.string().min(12).regex(/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)/),
  age: z.number().int().min(18).max(120),
});

// SQL Injection Prevention
const user = await db.query(
  'SELECT * FROM users WHERE id = $1',
  [userId] // Parameterized query
);
```

### Password Hashing
```python
from argon2 import PasswordHasher

ph = PasswordHasher()
hashed = ph.hash(password)

# Verify
try:
    ph.verify(hashed, password)
except VerifyMismatchError:
    raise AuthenticationError("Invalid password")
```

## SECURITY CHECKLIST
```
[ ] Input validation on all data
[ ] Parameterized queries (no SQL injection)
[ ] Output encoding (XSS prevention)
[ ] HTTPS everywhere
[ ] Secure authentication (MFA enabled)
[ ] Least privilege access
[ ] Security headers (CSP, HSTS)
[ ] Dependency scanning
[ ] Secrets in vault
[ ] Logging & monitoring
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| XSS | Unescaped output | Encode all user content |
| SQL injection | String concatenation | Use parameterized queries |
| CSRF | No token | Implement CSRF tokens |
| Auth bypass | Broken access control | Verify on every request |
