---
title: Linux Installation
visible_when:
  entitlements:
    - isEmbeddedClusterDownloadEnabled
---

# HelmFace Linux Installation

Install HelmFace on a Linux server using Embedded Cluster. This deployment method bundles Kubernetes, etcd, and all dependencies into a single binary, ideal for air-gapped environments or simplified operations.

## Requirements

See the [system requirements documentation](requirements) for the full list of prerequisites. At minimum:

- Ubuntu 20.04+ / RHEL 8+ / CentOS 8+
- 4 CPUs, 8GB RAM, 40GB disk minimum
- Root or sudo access
- Ports 30000, 80, 443 available (configurable during install)

## Configuration

Customize the options below. The install commands will update automatically based on your selections.

<NetworkAvailability installType="linux" />
<VersionSelector installType="linux" />

## Install

SSH into your target machine and run the following command as root or with sudo.

<LinuxInstallAssets />

## Verify Installation

Once the installer completes, it will print the URL for the admin console. Open it in your browser to finalize HelmFace setup.

<CommandBlock>
# Check that all HelmFace pods are running (should be in helmface namespace)
kubectl get pods -n helmface

# Access the Embedded Cluster Admin Console
echo "Admin Console: https://$(hostname):30000"

# HelmFace web interface is available at
echo "HelmFace: https://$(hostname)"
</CommandBlock>

<InstanceName />

## Post-Install Configuration

After installation:

1. **Access Admin Console** — Navigate to `https://<hostname>:30000` with your license file
2. **Configure HelmFace** — Review database, MinIO, and Valkey settings (pre-configured by default)
3. **Verify License** — Check Settings page in HelmFace UI to confirm entitlements (AI enhancer, air-gap support, etc.)
4. **Upload Test Chart** — Upload a sample Helm chart to verify the UI and schema generation
5. **Set Up Support Bundles** — Configure kubectl plugin for collecting diagnostics (see Support Bundles section)

HelmFace runs in the `helmface` namespace. Access the web UI at `https://<hostname>` (HTTPS enforced by Traefik).
