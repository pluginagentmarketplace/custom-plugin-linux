---
name: terraform
description: Infrastructure as Code skill - Terraform, state management, modules, multi-cloud
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [provision, plan, import, migrate, module] }
    provider: { type: string, enum: [aws, gcp, azure, kubernetes] }
  required: [task]

output_schema:
  type: object
  properties:
    hcl_code: { type: string }
    commands: { type: array }
    state_notes: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 120000
---

# Terraform Skill

## PURPOSE
Infrastructure provisioning with declarative configuration.

## CORE COMPETENCIES
```
Core Concepts:
├── Resources & Data Sources
├── Variables & Outputs
├── State management
├── Modules
└── Workspaces

Providers:
├── AWS
├── GCP
├── Azure
├── Kubernetes
└── Helm
```

## CODE PATTERNS

### Module Structure
```hcl
# modules/vpc/main.tf
resource "aws_vpc" "main" {
  cidr_block           = var.cidr_block
  enable_dns_hostnames = true

  tags = merge(var.tags, {
    Name = var.name
  })
}

# modules/vpc/variables.tf
variable "name" {
  type        = string
  description = "VPC name"
}

variable "cidr_block" {
  type        = string
  default     = "10.0.0.0/16"
  validation {
    condition     = can(cidrhost(var.cidr_block, 0))
    error_message = "Must be valid CIDR block."
  }
}

# modules/vpc/outputs.tf
output "vpc_id" {
  value       = aws_vpc.main.id
  description = "VPC ID"
}
```

### Remote State
```hcl
terraform {
  backend "s3" {
    bucket         = "terraform-state"
    key            = "prod/terraform.tfstate"
    region         = "us-east-1"
    encrypt        = true
    dynamodb_table = "terraform-locks"
  }
}
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| State lock | Concurrent run | `terraform force-unlock` |
| Drift | Manual changes | `terraform refresh` or import |
| Cycle | Circular deps | Review dependencies |
| Provider error | Auth issue | Check credentials |

## COMMANDS
```bash
terraform init
terraform plan -out=tfplan
terraform apply tfplan
terraform destroy

# State
terraform state list
terraform state show resource
terraform import resource.name id
```
