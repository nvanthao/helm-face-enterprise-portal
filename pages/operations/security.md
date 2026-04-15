---
title: Security
visible_when:
  permissions:
    - canViewSecurity
---

# HelmFace Security

HelmFace implements multiple layers of security to protect your deployment and data.

## License Validation & Expiry Enforcement

HelmFace uses the Replicated SDK to validate licenses and enforce expiry policies:

- **License Check** — On startup and periodically during operation, HelmFace queries the Replicated SDK for license validity
- **Expiry Warnings** — When a license expires within 30 days, a non-dismissible banner appears in the UI alerting operators
- **Hard Block** — When a license is fully expired, HelmFace blocks all functionality and displays a warning screen; the application does not render until license is renewed
- **Perpetual Licenses** — Licenses without an expiry date are always valid; no warnings or blocks apply

## Session Management

- **Valkey-Backed Sessions** — User sessions are stored in Valkey (Redis-compatible) with secure cookie-based authentication
- **Secure Cookies** — Session cookies use HttpOnly and Secure flags to prevent XSS and MITLS attacks
- **Cache Isolation** — Each session is isolated and cached separately in Valkey

## TLS & HTTPS

- **Traefik Ingress** — HelmFace runs behind Traefik ingress controller with automatic TLS termination
- **HTTPS Enforcement** — HTTP traffic is redirected to HTTPS; direct HTTP access is blocked
- **Certificate Management** — Deploy cert-manager alongside HelmFace to automatically provision and renew TLS certificates

## Data Protection

- **No Credential Storage** — HelmFace does not store MinIO, PostgreSQL, or Valkey credentials in the application database
- **Environment Variables** — Database and object storage credentials are injected via Kubernetes Secrets or environment variables
- **Helm Chart Encryption** — Charts uploaded to MinIO can be encrypted at rest using MinIO's SSE (Server-Side Encryption) feature

## Support Bundle Privacy

- **Local Collection** — Support bundles are collected locally on the user's machine using the kubectl plugin
- **User-Initiated Upload** — Bundles are not automatically uploaded; users explicitly trigger upload from the HelmFace UI (/support page)
- **Vendor Portal** — Bundles are uploaded to the Replicated vendor portal for analysis; only the vendor with API access can view them

## RBAC & Authorization

- **Replicated Permissions Model** — HelmFace respects Replicated KOTS/Embedded Cluster RBAC definitions
- **Role-Based Access** — Different user roles (admin, operator) have different permissions as defined in the Replicated app configuration

## Compliance & Best Practices

- **No PII in Logs** — HelmFace avoids logging personal identifiable information
- **Audit Trail** — Chart uploads, schema enhancements, and support bundle uploads are tracked
- **Vulnerability Scanning** — Container images are scanned for known CVEs before release
