---
name: security-engineer
description: This skill focuses on protecting code, infrastructure, and user data by adopting a "Shift Left" security mindset. It ensures security is integrated early in the development lifecycle rather than as an afterthought.
version: 1.0.0
---
## Overview
This skill focuses on protecting code, infrastructure, and user data by adopting a "Shift Left" security mindset. It ensures security is integrated early in the development lifecycle rather than as an afterthought.

## When to Use
- **Architecture Review**: Designing new systems or modifying existing ones.
- **Code Audit**: Reviewing code for vulnerabilities or logic flaws.
- **Authentication/Authorization**: Implementing or modifying login, registration, or permission systems.
- **Handling Secrets**: Managing API keys, database credentials, and other sensitive data.
- **Dependency Management**: Adding or updating third-party libraries.

## Core Principles

### 1. Least Privilege
Grant only the minimum access levels necessary for a user, process, or system to perform its function. Avoid "admin" or "root" access unless absolutely required.

### 2. Defense in Depth
Implement multiple layers of security controls (e.g., firewalls, validation, encryption, monitoring) so that if one fails, others are still in place.

### 3. Sanitize All Inputs
Never trust user data. Validate and sanitize all input from APIs, forms, and URL parameters to prevent Injection attacks (SQLi, XSS, etc.).

## Checklist
- [ ] **Secrets Management**: Are secrets (.env, credentials) excluded from git (via .gitignore)?
- [ ] **Rate Limiting**: Is the API rate-limited to prevent abuse and DoS attacks?
- [ ] **Vulnerability Scanning**: Are dependencies scanned for known vulnerabilities (e.g., `npm audit`, `cargo audit`, `pip-audit`)?
- [ ] **Transport Security**: Is HTTPS enforced for all communications?
- [ ] **Input Validation**: Are all inputs validated against strict schemas (e.g., Zod, Joi)?
- [ ] **Output Encoding**: Is data properly encoded before being rendered to prevent XSS?
- [ ] **Authentication**: Is strong authentication enforced (MFA, strong passwords)?
- [ ] **Authorization**: Are proper access controls (RBAC/ABAC) in place for every endpoint?
- [ ] **Logging & Monitoring**: Is security-relevant activity logged (without logging sensitive data)?
