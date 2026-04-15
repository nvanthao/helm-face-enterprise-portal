---
title: Frequently Asked Questions
---

# Frequently Asked Questions

## General

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
### What are the system requirements?

See [Requirements](../installation/requirements) for details.
{{/if}}

### How do I check for updates?

See [Checking for Updates](../updates/checking).

{{#if entitlements.isHelmInstallEnabled}}
## Installation

### Which installation method should I use?

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
Choose [Embedded Cluster (Linux)](../installation/linux) for installing on a Linux server, or [Helm](../installation/helm) for deploying to an existing Kubernetes cluster.
{{/if}}
{{/if}}

## Features & Entitlements

### Why is the "Enhance with AI" button disabled?

The AI schema enhancement feature requires the `ai_enhancer` entitlement in your license. Contact your vendor or support team to enable this capability. Check your license status in **Settings** → **License Information**.

### What is a support bundle and why do I need it?

A support bundle collects diagnostic information from your installation (logs, cluster state, metrics) to help troubleshoot issues faster. When contacting support, generating and uploading a bundle significantly speeds up diagnosis.

## Licensing & Expiry

### What happens when my license expires?

- **Within 30 days of expiry:** A warning banner appears in HelmFace prompting you to renew
- **On expiry date:** HelmFace blocks all functionality and displays an expiry screen; you must renew your license to regain access
- Renew your license through your vendor portal and redeploy or restart HelmFace

### Can I view my license details in HelmFace?

Yes. Open **Settings** (gear icon) and scroll to **License Information**. This shows:
- License ID
- Customer name
- License type
- Entitlements (AI enhancer, air-gap support, etc.)
- Expiry date (if applicable)

## Troubleshooting

### How do I collect diagnostic information?

Generate a support bundle for troubleshooting:

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
- [Linux installations](../operations/bundles/linux)
{{/if}}
{{#if entitlements.isHelmInstallEnabled}}
- [Helm installations](../operations/bundles/helm)
{{/if}}
- [Upload an existing bundle](../operations/bundles/uploaded)

### Embedded Cluster: Installation fails with "port 30080 already in use"

**Issue:** The Embedded Cluster TLS proxy binds to port 30080, which may conflict with other services (e.g., Traefik NodePort).

**Solution:**
1. Identify the process using port 30080: `sudo netstat -tlnp | grep 30080`
2. Either stop the conflicting service or choose a different port during installation
3. If installing via Admin Console, use the `--admin-console-port` flag to change the Admin Console port

### Embedded Cluster: Upgrade fails with "pending revision" error

**Issue:** After a failed Helm release upgrade, subsequent upgrade attempts fail with `failed to stat pending revision directory`.

**Solution:**
1. Wait a few minutes, then retry the upgrade from the Admin Console
2. If the error persists, the system may need to clear stale state — contact support with the error details
3. Provide a support bundle to help diagnose the root cause

### Admin Console: Config fields marked "read-only" are still editable

**Note:** In some versions of Embedded Cluster, the `readonly` property in config fields may not be visually enforced in the Admin Console UI. However, read-only fields should not be modified. If you encounter this:
1. Do not modify fields marked as vendor-controlled
2. Contact your vendor if you need to override a locked setting
3. Check the HelmFace Settings page for the correct configuration

### Chart upload fails with validation error

**Issue:** Uploaded Helm chart fails validation or is rejected.

**Common causes:**
- Chart is not a valid `.tgz` (gzipped tar archive) — ensure file format is correct
- Chart size exceeds limits — most charts under 100MB upload without issue
- Chart is missing required files (Chart.yaml, values.yaml)

**Solution:**
1. Verify the chart with: `helm lint /path/to/chart`
2. Package the chart: `helm package /path/to/chart`
3. Upload the resulting `.tgz` file

### How do I update HelmFace?

See [Checking for Updates](../updates/checking) for version-specific instructions. In summary:
- **Embedded Cluster:** Use the Admin Console → Check for Updates → Deploy Update button
- **Helm:** Run `helm upgrade helmface helmface/helmface -n helmface -f values.yaml`
