---
title: Release History
---

# Release History

Track all HelmFace updates, security patches, and feature releases.

## v0.3.0 (Current)

**Release Date:** April 2026

Core feature release with enterprise capabilities and operational excellence.

### Key Features
- **Chart Management** — Upload, store, and manage Helm charts with automatic schema generation
- **Two-Tier Schema Generation** — Basic (auto) and AI-enhanced (via Anthropic Claude with `ai_enhancer` entitlement)
- **Interactive Configuration Forms** — JSON Schema form rendering from values.yaml
- **Support Bundle Collection** — Local collection + browser upload to Replicated vendor portal
- **License Entitlement Gates** — Feature access controlled by: `ai_enhancer`, `isEmbeddedClusterDownloadEnabled`, `isHelmInstallEnabled`, `isAirgapSupported`
- **License Expiry Enforcement** — Warnings at 30 days, hard blocks on expiry
- **App Update Notifications** — Checks for updates via Replicated SDK
- **Settings Page** — View license info, available updates, and entitlements

### Deployment Options
- Docker Compose (local/testing)
- Kubernetes with Helm chart
- Replicated/KOTS (enterprise with Admin Console)

### Technology Stack
- Next.js 16, React 19, TypeScript, Tailwind CSS v4, shadcn/ui
- PostgreSQL, MinIO, Valkey/Redis
- Anthropic Claude SDK for AI enhancements
- React JSONSchema Form (RJSF) for UI rendering

<ReleaseHistory />
