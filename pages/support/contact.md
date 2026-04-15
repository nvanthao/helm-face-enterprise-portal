---
title: Contact Support
---

# Contact Support

Get help from our support team. Before reaching out, please prepare the information below to speed up resolution.

<ContactInfo />

## Before Contacting Support

Have the following information ready when opening a support case:

### HelmFace Details
- **HelmFace Version** — Check in **Settings** → **Available Updates** section
- **License ID** — Visible in **Settings** → **License Information**
- **Installation Type** — Embedded Cluster (Linux) or Helm?
- **Chart Name & Version** — Name of the Helm chart you were configuring
- **Error Message** — Exact error text shown in the UI or logs

### Support Bundle
Generate a support bundle for significantly faster diagnosis:

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
   - [Linux (Embedded Cluster)](../operations/bundles/linux) — Follow instructions to collect and upload
{{/if}}
{{#if entitlements.isHelmInstallEnabled}}
   - [Helm](../operations/bundles/helm) — Follow instructions to collect and upload
{{/if}}

Once generated, you can [upload it here](../operations/bundles/uploaded) and reference the bundle ID in your support case.

### Cluster/Node Information
{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
- **Node Hostname & IP address**
- **Linux Distribution** (Ubuntu 20.04+, RHEL 8+, etc.)
- **Kubernetes Version** — Run `kubectl version` on the node
- **Disk & Memory Available** — Run `df -h` and `free -h`
{{/if}}
{{#if entitlements.isHelmInstallEnabled}}
- **Kubernetes Distribution** (EKS, GKE, on-prem, etc.)
- **Kubernetes Version** — Run `kubectl version`
- **Helm Version** — Run `helm version`
- **Namespace** — Which namespace is HelmFace installed in?
{{/if}}

### Reproduction Steps

Include step-by-step instructions to reproduce the issue:
1. What action triggered the error?
2. What was the expected behavior?
3. What actually happened?

## FAQ

Check the [FAQ](../support/faq) for answers to common questions about features, licensing, installation, and troubleshooting.
