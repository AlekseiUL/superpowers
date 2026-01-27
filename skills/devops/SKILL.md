---
name: devops
version: 1.0.0
description: Use when managing infrastructure, configuring Docker, setting up CI/CD pipelines, or deploying applications.
---


# DevOps & Infrastructure

## Overview
Standardizes infrastructure management, containerization, and deployment pipelines. Enforces security, immutability, and observability in all infrastructure deliverables.

## When to Use
- Creating or editing Dockerfiles
- Setting up GitHub Actions or CI/CD pipelines
- configuring server deployments
- Setting up monitoring/logging
- Managing Infrastructure as Code (Terraform/Ansible)

## Core Practices

### 1. Immutable Infrastructure
- **Containers**: Use Docker for all services.
- **Versioning**: Pin all tags (no `:latest`).
- **Config**: Inject config via environment variables, not baked files.

### 2. Infrastructure as Code (IaC)
- Define all infrastructure in code (Terraform, Ansible, CloudFormation).
- Manual server changes are forbidden.

### 3. Observability
- **Logs**: JSON format, stdout/stderr only (no local log files).
- **Metrics**: Expose Prometheus-compatible metrics.
- **Health**: Every service must expose a health check endpoint.

## Checklist (MANDATORY)

Before marking any DevOps task complete, verify:

- [ ] **Docker**: Uses multi-stage builds (builder vs runner)
- [ ] **Docker**: Contains explicit `HEALTHCHECK` instruction
- [ ] **Docker**: Runs as non-root user
- [ ] **Security**: No secrets in code or docker history (use build args/secrets)
- [ ] **CI/CD**: Linting and tests run before build/deploy
- [ ] **CI/CD**: Builds are deterministic (lockfiles used)

## Common Mistakes
- **Skipping Healthchecks**: "I'll add it later" -> **Add it now.**
- **Single Stage Builds**: "It's a small app" -> **Use multi-stage to strip build tools.**
- **Root User**: "It's easier" -> **Create a specific user.**
- **Secrets**: `ENV API_KEY=...` in Dockerfile -> **FORBIDDEN. Use runtime env or build secrets.**

## Example: Production Dockerfile

```dockerfile
# Stage 1: Builder
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Stage 2: Runner
FROM node:18-alpine
WORKDIR /app
# Install minimal production deps
COPY package*.json ./
RUN npm ci --only=production
# Copy built artifacts
COPY --from=builder /app/dist ./dist
# Security: Non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser
# Observability: Healthcheck
HEALTHCHECK --interval=30s --timeout=3s \
  CMD wget --quiet --tries=1 --spider http://localhost:3000/health || exit 1
# Start
CMD ["node", "dist/main.js"]
```
