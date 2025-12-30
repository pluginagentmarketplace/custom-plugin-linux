---
name: architecture
description: System architecture skill - Design patterns, scalability, distributed systems
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [design, review, scale, optimize, migrate] }
    scale: { type: string, enum: [startup, growth, enterprise] }
  required: [task]

output_schema:
  type: object
  properties:
    architecture: { type: string }
    diagram: { type: string }
    tradeoffs: { type: object }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 60000
---

# System Architecture Skill

## PURPOSE
System design, scalability patterns, and distributed systems.

## CORE COMPETENCIES
```
Patterns:
├── Monolith → Microservices
├── Event-Driven
├── CQRS / Event Sourcing
├── Saga Pattern
└── Circuit Breaker

Scalability:
├── Horizontal scaling
├── Database sharding
├── Caching layers
├── Load balancing
└── CDN

Reliability:
├── Fault tolerance
├── Disaster recovery
├── Chaos engineering
└── SLOs/SLIs
```

## DESIGN PATTERNS

### Microservices Communication
```
Sync:
├── REST/gRPC between services
├── Service discovery
└── Load balancing

Async:
├── Message queues (RabbitMQ, SQS)
├── Event streaming (Kafka)
└── Pub/Sub patterns
```

### Database Patterns
```
Read Scaling:
├── Read replicas
├── Caching (Redis)
└── CDN for static

Write Scaling:
├── Sharding
├── Write-ahead log
└── Event sourcing
```

## SYSTEM DESIGN TEMPLATE
```
1. Requirements clarification
2. Capacity estimation
3. High-level design
4. Detailed component design
5. Bottleneck identification
6. Scaling strategy
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| Single point of failure | No redundancy | Add replicas, failover |
| Cascading failures | No isolation | Circuit breaker, bulkhead |
| Data inconsistency | Eventual consistency | Saga, compensating txns |
