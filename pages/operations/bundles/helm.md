---
title: Helm Support Bundles
visible_when:
  entitlements:
    - isHelmInstallEnabled
---

# HelmFace Helm Support Bundles

Collect and view support bundles from your Helm-based Kubernetes installations for troubleshooting and support escalation.

## About Support Bundles

HelmFace's support bundle feature collects diagnostic information from your cluster to help troubleshoot issues:

**Typical contents:**
- Pod logs from the `helmface` namespace
- Kubernetes deployment and service state
- Node resource utilization and health
- Helm release information and status
- Recent API request logs

## Collection Process

1. Visit the **Support** page in HelmFace (`/support`)
2. Follow the on-screen instructions to install the kubectl plugin: `kubectl krew install support-bundle`
3. Run the provided collection command (automatically updates based on your Kubernetes cluster context)
4. A `support-bundle-*.tar.gz` file is generated locally on your machine
5. Upload the bundle via the HelmFace UI for instant upload to the Replicated vendor portal

## Uploading Bundles

Bundles can be uploaded directly from HelmFace's support page or via the [Upload Bundles](../operations/bundles/uploaded) section. Once uploaded:
- Bundle ID and slug are displayed for reference
- Vendor can view and analyze the bundle in the Replicated portal
- Technical support team can diagnose issues faster

<HelmBundles />
