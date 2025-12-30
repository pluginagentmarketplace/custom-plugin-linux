---
name: docker
description: Docker containerization skill - Images, Compose, security, optimization
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [build, debug, optimize, security, compose] }
    base_image: { type: string }
  required: [task]

output_schema:
  type: object
  properties:
    dockerfile: { type: string }
    commands: { type: array }
    security_notes: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 60000
---

# Docker Skill

## PURPOSE
Container image building, optimization, and orchestration.

## CORE COMPETENCIES
```
Dockerfile:
├── Multi-stage builds
├── Layer caching
├── Build arguments
└── Health checks

Docker Compose:
├── Service definition
├── Networks
├── Volumes
└── Environment management

Security:
├── Non-root users
├── Minimal base images
├── Secret management
└── Image scanning
```

## CODE PATTERNS

### Multi-Stage Build
```dockerfile
# Build stage
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build

# Production stage
FROM node:20-alpine
RUN addgroup -g 1001 app && adduser -u 1001 -G app -s /bin/sh -D app
USER app
WORKDIR /app
COPY --from=builder --chown=app:app /app/dist ./dist
COPY --from=builder --chown=app:app /app/node_modules ./node_modules
EXPOSE 3000
HEALTHCHECK --interval=30s CMD wget -q --spider http://localhost:3000/health
CMD ["node", "dist/main.js"]
```

### Docker Compose
```yaml
version: '3.8'
services:
  app:
    build: .
    ports: ["3000:3000"]
    environment:
      - NODE_ENV=production
    depends_on:
      db:
        condition: service_healthy
    healthcheck:
      test: ["CMD", "wget", "-q", "--spider", "http://localhost:3000/health"]
      interval: 30s
      retries: 3

  db:
    image: postgres:16-alpine
    volumes:
      - pgdata:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres"]

volumes:
  pgdata:
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| Build slow | No cache | Order layers by change frequency |
| Image large | Too many layers | Use multi-stage, alpine |
| Container exits | App crash | Check logs, add health check |
| Permission denied | Root vs user | Use non-root user |

## COMMANDS
```bash
# Build
docker build -t app:latest .

# Run with limits
docker run -d --memory=512m --cpus=1 app:latest

# Debug
docker logs -f container_id
docker exec -it container_id sh

# Cleanup
docker system prune -af
```
