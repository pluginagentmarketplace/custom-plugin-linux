---
name: kubernetes
description: Kubernetes orchestration skill - Deployments, services, security, scaling
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [deploy, debug, scale, secure, monitor] }
    resource_type: { type: string }
  required: [task]

output_schema:
  type: object
  properties:
    manifests: { type: array }
    commands: { type: array }
    troubleshooting: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 60000
---

# Kubernetes Skill

## PURPOSE
Container orchestration, deployment, and cluster management.

## CORE COMPETENCIES
```
Workloads:
├── Deployments
├── StatefulSets
├── DaemonSets
├── Jobs/CronJobs
└── ReplicaSets

Networking:
├── Services (ClusterIP, NodePort, LoadBalancer)
├── Ingress
├── NetworkPolicies
└── Service Mesh

Configuration:
├── ConfigMaps
├── Secrets
├── PersistentVolumes
└── StorageClasses

Security:
├── RBAC
├── Pod Security Standards
├── Network Policies
└── Secrets encryption
```

## CODE PATTERNS

### Production Deployment
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: app
spec:
  replicas: 3
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 0
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      securityContext:
        runAsNonRoot: true
        runAsUser: 1000
      containers:
      - name: app
        image: app:v1.0.0
        ports:
        - containerPort: 8080
        resources:
          requests:
            memory: "128Mi"
            cpu: "100m"
          limits:
            memory: "256Mi"
            cpu: "500m"
        livenessProbe:
          httpGet:
            path: /health
            port: 8080
          initialDelaySeconds: 30
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /ready
            port: 8080
          initialDelaySeconds: 5
        env:
        - name: DB_HOST
          valueFrom:
            configMapKeyRef:
              name: app-config
              key: db_host
```

### Service & Ingress
```yaml
apiVersion: v1
kind: Service
metadata:
  name: app
spec:
  selector:
    app: myapp
  ports:
  - port: 80
    targetPort: 8080
---
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: app
  annotations:
    cert-manager.io/cluster-issuer: letsencrypt
spec:
  tls:
  - hosts: [app.example.com]
    secretName: app-tls
  rules:
  - host: app.example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: app
            port:
              number: 80
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| CrashLoopBackOff | App crash | Check logs: `kubectl logs pod` |
| ImagePullBackOff | Registry auth | Check secrets, image name |
| Pending | No resources | Check nodes, resource requests |
| OOMKilled | Memory limit | Increase limits, optimize app |

## COMMANDS
```bash
# Debug
kubectl get pods -w
kubectl describe pod <name>
kubectl logs -f <pod> --previous
kubectl exec -it <pod> -- sh

# Scale
kubectl scale deploy app --replicas=5
kubectl autoscale deploy app --min=2 --max=10 --cpu-percent=80

# Rollback
kubectl rollout undo deploy app
kubectl rollout status deploy app
```
