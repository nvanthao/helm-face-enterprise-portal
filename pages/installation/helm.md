---
title: Helm Installation
visible_when:
  entitlements:
    - isHelmInstallEnabled
---

# HelmFace Helm Installation

Install HelmFace on an existing Kubernetes cluster using Helm charts. This method is ideal for teams with mature Kubernetes infrastructure and existing cluster management workflows.

## Requirements

Review the following prerequisites before installing.

- Kubernetes cluster v1.28 or later
- Helm 3.x installed on your workstation
- kubectl configured with cluster access
- StorageClass available for persistent volumes
- PostgreSQL database (external or managed)
- MinIO S3-compatible object storage (for chart storage)
- Valkey/Redis instance (for session caching)

## Configuration

Customize the options below. The install commands will update automatically based on your selections.

<KubernetesDistribution />
<NetworkAvailability installType="helm" />
<RegistryAccess />
<VersionSelector installType="helm" />

## Install

<HelmInstallAssets />

<InstanceName />

## Helm Chart Values

When installing, you must configure the following values:

```yaml
app:
  replicaCount: 3
  anthropicApiKey: "sk-ant-..."  # Provided by vendor entitlement
  
database:
  url: "postgresql://user:password@postgres.example.com:5432/helmface"
  
minio:
  endpoint: "minio.example.com:9000"
  accessKey: "minioadmin"
  secretKey: "minioadmin"
  bucket: "helm-charts"
  
valkey:
  url: "redis://valkey.example.com:6379"
```

HelmFace runs in the `helmface` namespace by default. Update this value to deploy to a different namespace.

## Post-Install

After installation:

1. Verify all pods are running: `kubectl get pods -n helmface`
2. Forward the service port: `kubectl port-forward -n helmface svc/helmface 3000:3000`
3. Access HelmFace at `http://localhost:3000` (or configure ingress for external access)
4. Configure ingress with TLS termination (recommended)
5. Set up support bundle collection by installing the kubectl plugin (see Support Bundles section)
