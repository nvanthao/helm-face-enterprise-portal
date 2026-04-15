---
title: Checking for Updates
---

# Checking for HelmFace Updates

HelmFace checks for available updates via the Replicated SDK and notifies operators when new versions are available.

## Automatic Update Checks

HelmFace automatically checks for new releases on startup and periodically during operation. When a new version is available:
- An update badge appears in the HelmFace navigation (top bar)
- A dismissible notification banner is shown with the version label and release notes summary
- The **Settings** page displays a full list of available updates with release notes

## Viewing Available Updates

1. Open HelmFace and navigate to **Settings** (gear icon in top right)
2. Scroll to "Available Updates" section
3. View the new version label, release date, and full release notes
4. Click "Check for Updates" to manually refresh

## Applying Updates

### For Embedded Cluster (Linux)

1. Access the Embedded Cluster Admin Console at `https://<hostname>:30000`
2. Click **Check for Updates** in the top right
3. When a new version is available, click **Deploy Update**
4. The system applies the update and verifies all pods are running

### For Helm Installations

1. Fetch the latest Helm chart from the repository
2. Run: `helm upgrade helmface helmface/helmface -n helmface -f values.yaml`
3. Monitor pod rollout: `kubectl rollout status deployment/helmface -n helmface`

## Release Channels

HelmFace releases follow a staged deployment process:
- **Unstable** — Latest development builds; for testing only
- **Beta** — Pre-release versions; recommended for non-production environments
- **Stable** — Production-ready releases; recommended for all deployments

Your license determines which channels you can access.

<LinuxUpdateAssets />
<HelmUpdateAssets />
