---
title: Linux Support Bundles
visible_when:
  entitlements:
    - isEmbeddedClusterDownloadEnabled
---

# HelmFace Linux Support Bundles

Collect and view support bundles from your Linux (Embedded Cluster) installations for troubleshooting and support escalation.

## About Support Bundles

HelmFace's support bundle feature collects diagnostic information from your Embedded Cluster to help troubleshoot issues:

**Typical contents:**
- Pod logs from the `helmface` namespace
- Embedded Cluster logs and health state
- Kubernetes API logs and event history
- Helm release information and HelmFace deployment status
- Node resource utilization, disk usage, and system metrics
- HelmFace database and MinIO connectivity checks

## Collection Process (Embedded Cluster)

1. Visit the **Support** page in HelmFace (accessible at `https://<hostname>/support`)
2. Follow the on-screen instructions to install the kubectl plugin: `kubectl krew install support-bundle`
3. Run the provided collection command to gather cluster diagnostics
4. A `support-bundle-*.tar.gz` file is generated in your current directory
5. Upload the bundle via the HelmFace UI for instant upload to the Replicated vendor portal

## Uploading Bundles

Bundles can be uploaded directly from HelmFace's support page or via the [Upload Bundles](../operations/bundles/uploaded) section. Once uploaded:
- Bundle ID and slug are displayed for reference
- Vendor can view and analyze the bundle in the Replicated portal
- Technical support team can diagnose issues faster with full cluster context

<LinuxBundles />
