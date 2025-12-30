---
name: cloud
description: Cloud platforms skill - AWS, GCP, Azure core services and architecture
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [design, deploy, optimize, migrate, cost] }
    platform: { type: string, enum: [aws, gcp, azure] }
  required: [task, platform]

output_schema:
  type: object
  properties:
    architecture: { type: string }
    services: { type: array }
    cost_estimate: { type: object }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 60000
---

# Cloud Platforms Skill

## PURPOSE
Cloud architecture and services across major providers.

## CORE SERVICES

### AWS
```
Compute: EC2, Lambda, ECS, EKS
Storage: S3, EBS, EFS
Database: RDS, DynamoDB, ElastiCache
Networking: VPC, ALB, CloudFront, Route53
```

### GCP
```
Compute: Compute Engine, Cloud Run, GKE
Storage: Cloud Storage, Persistent Disk
Database: Cloud SQL, Firestore, Memorystore
Networking: VPC, Cloud Load Balancing, Cloud CDN
```

### Azure
```
Compute: VMs, Container Apps, AKS
Storage: Blob Storage, Disk
Database: SQL Database, Cosmos DB
Networking: VNet, Application Gateway
```

## ARCHITECTURE PATTERNS

### 3-Tier Web App
```
┌─────────────────────────────────────┐
│           CloudFront/CDN            │
├─────────────────────────────────────┤
│        Application Load Balancer     │
├─────────────────────────────────────┤
│     Auto Scaling Group (EC2/ECS)    │
├─────────────────────────────────────┤
│   RDS Multi-AZ + ElastiCache Redis  │
└─────────────────────────────────────┘
```

## COST OPTIMIZATION
```
Compute:
├── Reserved/Committed instances
├── Spot/Preemptible for batch
├── Right-sizing
└── Auto-scaling

Storage:
├── Lifecycle policies
├── Tiered storage
└── Delete unused

Network:
├── NAT gateway sharing
├── VPC endpoints
└── Regional resources
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| High cost | Over-provisioned | Right-size, reservations |
| Latency | Region distance | Multi-region, CDN |
| Permission denied | IAM policy | Review policies |
