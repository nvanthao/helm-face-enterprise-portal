---
title: Documentation
---

# HelmFace Documentation

Welcome to HelmFace, a web-based Helm chart management tool that transforms Helm charts into interactive configuration forms. This personalized documentation portal is customized based on your license entitlements.

## What is HelmFace?

HelmFace provides a visual interface for generating, storing, and managing Helm chart values. Upload a chart, and HelmFace automatically generates a JSON Schema-based configuration form. Optionally enhance schemas with AI-powered suggestions via Claude to capture intent beyond raw YAML defaults.

**Key capabilities:**
- Chart upload and metadata management with schema generation
- Two-tier schema support: basic (auto-generated) and AI-enhanced (with `ai_enhancer` entitlement)
- Interactive configuration forms rendering Helm values
- Support bundle collection for diagnostics and support portal upload
- License entitlement gates for feature access
- App update notifications and license management

## Available Features

Your installation includes access to the following features:

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
- **Linux (Embedded Cluster):** Single-node or multi-node Kubernetes via Embedded Cluster on Linux servers
{{/if}}
{{#if entitlements.isHelmInstallEnabled}}
- **Helm Installation:** Deploy to existing Kubernetes clusters using Helm charts
{{/if}}
{{#if entitlements.isAirgapSupported}}
- **Air Gap Support:** Install in disconnected, air-gapped environments
{{/if}}
{{#if entitlements.ai_enhancer}}
- **AI Schema Enhancement:** Unlock advanced schema inference via Anthropic Claude for more intuitive configuration forms
{{/if}}

## Getting Started

Use the sidebar navigation on the left to explore documentation sections. We recommend starting with:

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
1. **Installation Requirements** — Review system requirements and prerequisites for Embedded Cluster installations
{{/if}}
2. **Installation Guide** — Follow step-by-step installation instructions for your deployment method
3. **Settings & License** — View license status, entitlements, and available updates
4. **Support Bundles** — Collect and upload diagnostic bundles for troubleshooting
5. **FAQ** — Check common questions and known issues

## Quick Links

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
- [Installation Requirements](installation/requirements)
- [Linux Installation](installation/linux)
{{/if}}
{{#if entitlements.isHelmInstallEnabled}}
- [Helm Installation](installation/helm)
{{/if}}
- [Release History](installation/release-history)
- [Check for Updates](updates/checking)
- [Support Bundles](operations/bundles/uploaded)
- [FAQ](support/faq)
