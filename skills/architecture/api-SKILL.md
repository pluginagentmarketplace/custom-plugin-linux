---
name: api
description: API design skill - REST, GraphQL, gRPC, documentation
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [design, implement, document, optimize, version] }
    style: { type: string, enum: [rest, graphql, grpc] }
  required: [task]

output_schema:
  type: object
  properties:
    schema: { type: string }
    code: { type: string }
    documentation: { type: string }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 30000
---

# API Design Skill

## PURPOSE
API design, implementation, and documentation.

## CORE COMPETENCIES
```
REST:
├── Resource naming
├── HTTP methods
├── Status codes
├── Versioning
├── Pagination
└── HATEOAS

GraphQL:
├── Schema design
├── Queries & Mutations
├── Subscriptions
├── DataLoader
└── Federation

gRPC:
├── Protocol Buffers
├── Streaming
├── Error handling
└── Load balancing
```

## CODE PATTERNS

### REST Design
```yaml
# OpenAPI 3.1
/users:
  get:
    summary: List users
    parameters:
      - name: page
        in: query
        schema: { type: integer, default: 1 }
      - name: limit
        in: query
        schema: { type: integer, default: 20, maximum: 100 }
    responses:
      200:
        description: Success
        content:
          application/json:
            schema:
              type: object
              properties:
                data: { type: array, items: { $ref: '#/components/schemas/User' } }
                meta: { $ref: '#/components/schemas/Pagination' }
```

### GraphQL Schema
```graphql
type Query {
  users(first: Int, after: String): UserConnection!
  user(id: ID!): User
}

type User {
  id: ID!
  email: String!
  posts(first: Int): PostConnection!
}

type UserConnection {
  edges: [UserEdge!]!
  pageInfo: PageInfo!
}
```

## BEST PRACTICES
```
REST:
├── Use nouns for resources
├── HTTP verbs for actions
├── Consistent error format
├── Version in URL or header
└── Rate limiting

GraphQL:
├── Avoid N+1 with DataLoader
├── Limit query depth
├── Paginate connections
└── Use fragments
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| N+1 queries | No batching | Use DataLoader |
| Slow response | Over-fetching | Select only needed fields |
| Breaking change | No versioning | Version your API |
