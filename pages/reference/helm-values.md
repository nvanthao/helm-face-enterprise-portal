---
title: Helm Chart Reference
---

# HelmFace Helm Chart Reference

> Auto-generated from [`values.yaml`](https://github.com/nvanthao/helm-face/blob/main/helm/helmface/values.yaml). Do not edit manually — changes are overwritten on each release.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| replicaCount | int | `1` | Number of HelmFace pod replicas |
| image.repository | string | `"images.quirkyquokka.dev/proxy/helm-face/ghcr.io/nvanthao/helm-face"` | Container image repository |
| image.pullPolicy | string | `"Always"` | Image pull policy |
| image.tag | string | `"main"` | Image tag. Overrides Chart.appVersion when set |
| imagePullSecrets | list | `[]` | List of image pull secrets for private registries |
| nameOverride | string | `""` | Partial name override for generated resources |
| fullnameOverride | string | `""` | Full name override for generated resources |
| app.anthropicApiKey | string | `""` | Anthropic API key (Option A: direct value). Leave empty to skip |
| app.anthropicApiKeySecret.name | string | `""` | Name of an existing K8s Secret containing the Anthropic API key |
| app.anthropicApiKeySecret.key | string | `"ANTHROPIC_API_KEY"` | Key within the Secret that holds the API key value |
| app.logLevel | string | `"info"` | Pino log level. Options: trace | debug | info | warn | error |
| app.showKotsConfigTab | bool | `true` | Show the KOTS Config Values tab in the UI |
| app.minioBucket | string | `"helm-charts"` | MinIO bucket name used for chart storage |
| app.externalMinio.endpoint | string | `""` | External MinIO endpoint (used when minio.enabled=false) |
| app.externalMinio.accessKey | string | `""` | External MinIO access key |
| app.externalMinio.secretKey | string | `""` | External MinIO secret key |
| app.externalValkeyURL | string | `""` | External Valkey/Redis URL (used when valkey.enabled=false) |
| app.externalDatabase.host | string | `""` | External PostgreSQL host (used when cnpgCluster.enabled=false) |
| app.externalDatabase.port | string | `"5432"` | External PostgreSQL port |
| app.externalDatabase.name | string | `""` | External PostgreSQL database name |
| app.externalDatabase.username | string | `""` | External PostgreSQL username |
| app.externalDatabase.password | string | `""` | External PostgreSQL password |
| serviceAccount.create | bool | `true` | Create a dedicated ServiceAccount for HelmFace |
| serviceAccount.automount | bool | `true` | Automount the ServiceAccount token into pods |
| serviceAccount.annotations | object | `{}` | Annotations to add to the ServiceAccount |
| serviceAccount.name | string | `""` | Override the generated ServiceAccount name |
| podAnnotations | object | `{}` |  |
| podLabels | object | `{}` | Extra labels to add to HelmFace pods |
| podSecurityContext.fsGroup | int | `1001` | fsGroup applied to the pod's volume mounts |
| podSecurityContext.runAsNonRoot | bool | `true` | Require non-root user for all containers |
| securityContext.runAsNonRoot | bool | `true` | Run the container as non-root |
| securityContext.runAsUser | int | `1001` | UID for the container process |
| securityContext.allowPrivilegeEscalation | bool | `false` | Prevent privilege escalation |
| securityContext.readOnlyRootFilesystem | bool | `true` | Mount root filesystem as read-only |
| securityContext.capabilities.drop | list | `["ALL"]` | Linux capabilities to drop (drop ALL by default) |
| service.type | string | `"ClusterIP"` | Kubernetes Service type |
| service.port | int | `3000` | Service port (maps to container port 3000) |
| service.nodePort | string | `""` | NodePort value (only used when type=NodePort, range 30000–32767) |
| ingress.enabled | bool | `false` | Enable Ingress resource creation |
| ingress.className | string | `""` | IngressClass name (e.g. nginx, traefik) |
| ingress.annotations | object | `{}` | Annotations to add to the Ingress resource |
| ingress.hostname | string | `"helmface.example.com"` | Default hostname used when hosts[].host is empty |
| ingress.hosts | list | `[{"host":"","paths":[{"path":"/","pathType":"Prefix"}]}]` | Ingress host rules |
| ingress.tls.enabled | bool | `false` | Enable TLS on the Ingress |
| ingress.tls.mode | string | `""` | TLS mode: selfSigned | byo | certManager |
| ingress.tls.cert | string | `""` | PEM-encoded certificate (byo mode only) |
| ingress.tls.key | string | `""` | PEM-encoded private key (byo mode only) |
| ingress.tls.certManager.issuerName | string | `"letsencrypt-prod"` | cert-manager ClusterIssuer name (certManager mode only) |
| ingress.tls.certManager.acmeEmail | string | `""` | ACME email address required for cert-manager HTTP-01 challenge |
| resources.requests.cpu | string | `"250m"` | CPU request for the HelmFace container |
| resources.requests.memory | string | `"256Mi"` | Memory request for the HelmFace container |
| resources.limits.cpu | string | `"1000m"` | CPU limit for the HelmFace container |
| resources.limits.memory | string | `"512Mi"` | Memory limit for the HelmFace container |
| migrateResources | object | `{"limits":{"cpu":"250m","memory":"256Mi"},"requests":{"cpu":"100m","memory":"128Mi"}}` | Resource requests/limits for the db-migrate initContainer |
| migrateResources.requests.cpu | string | `"100m"` | CPU request for the db-migrate initContainer |
| migrateResources.requests.memory | string | `"128Mi"` | Memory request for the db-migrate initContainer |
| migrateResources.limits.cpu | string | `"250m"` | CPU limit for the db-migrate initContainer |
| migrateResources.limits.memory | string | `"256Mi"` | Memory limit for the db-migrate initContainer |
| startupProbe | object | `{"failureThreshold":30,"httpGet":{"path":"/api/health","port":"http"},"periodSeconds":10,"timeoutSeconds":5}` | Configure the startup probe (guards liveness until initial migrations complete) |
| startupProbe.failureThreshold | int | `30` | Number of failures before the pod is restarted (startupProbe × periodSeconds = max startup time) |
| startupProbe.periodSeconds | int | `10` | Interval between startup probe checks (seconds) |
| startupProbe.timeoutSeconds | int | `5` | Probe timeout (seconds) |
| livenessProbe | object | `{"failureThreshold":3,"httpGet":{"path":"/api/health","port":"http"},"initialDelaySeconds":0,"periodSeconds":15,"timeoutSeconds":5}` | Configure the liveness probe (restarts the pod when the app is unhealthy) |
| livenessProbe.initialDelaySeconds | int | `0` | Initial delay before starting liveness checks (seconds; startupProbe guards this) |
| livenessProbe.periodSeconds | int | `15` | Interval between liveness checks (seconds) |
| livenessProbe.timeoutSeconds | int | `5` | Probe timeout (seconds) |
| livenessProbe.failureThreshold | int | `3` | Failures before the pod is restarted |
| readinessProbe | object | `{"failureThreshold":3,"httpGet":{"path":"/api/health","port":"http"},"initialDelaySeconds":0,"periodSeconds":10,"timeoutSeconds":3}` | Configure the readiness probe (removes pod from service endpoints when not ready) |
| readinessProbe.initialDelaySeconds | int | `0` | Initial delay before starting readiness checks (seconds) |
| readinessProbe.periodSeconds | int | `10` | Interval between readiness checks (seconds) |
| readinessProbe.timeoutSeconds | int | `3` | Probe timeout (seconds) |
| readinessProbe.failureThreshold | int | `3` | Failures before the pod is removed from service endpoints |
| autoscaling.enabled | bool | `false` | Enable Horizontal Pod Autoscaler |
| autoscaling.minReplicas | int | `2` | Minimum replicas when autoscaling is enabled |
| autoscaling.maxReplicas | int | `10` | Maximum replicas when autoscaling is enabled |
| autoscaling.targetCPUUtilizationPercentage | int | `80` | Target CPU utilization percentage for scaling trigger |
| nodeSelector | object | `{}` | Node selector for pod scheduling |
| tolerations | list | `[]` | Tolerations for pod scheduling |
| affinity | object | `{}` | Affinity rules for pod scheduling |
| cnpgCluster.enabled | bool | `true` | Create a CloudNative PG Cluster CR for the app database |
| cnpgCluster.name | string | `"helmface-pg"` | Name of the CNPG Cluster resource |
| cnpgCluster.instances | int | `1` | Number of PostgreSQL instances (use 3 for HA) |
| cnpgCluster.storage.size | string | `"10Gi"` | PVC size for each PostgreSQL instance |
| cnpgCluster.storage.storageClass | string | `""` | StorageClass for PostgreSQL PVCs (empty = cluster default) |
| cnpgCluster.resources.requests.cpu | string | `"100m"` | CPU request for each PostgreSQL instance |
| cnpgCluster.resources.requests.memory | string | `"256Mi"` | Memory request for each PostgreSQL instance |
| cnpgCluster.resources.limits.cpu | string | `"500m"` | CPU limit for each PostgreSQL instance |
| cnpgCluster.resources.limits.memory | string | `"512Mi"` | Memory limit for each PostgreSQL instance |
| cloudnative-pg.enabled | bool | `true` | Install the CNPG operator subchart (set false if operator is already cluster-wide) |
| cloudnative-pg.crds.create | bool | `false` | Let the parent chart's crds/ directory manage CRD installation |
| cloudnative-pg.webhook.mutating.failurePolicy | string | `"Ignore"` | Failure policy for the CNPG mutating webhook (Ignore = non-blocking if webhook is unavailable) |
| cloudnative-pg.webhook.validating.failurePolicy | string | `"Ignore"` | Failure policy for the CNPG validating webhook (Ignore = non-blocking if webhook is unavailable) |
| minio.enabled | bool | `true` | Deploy bundled MinIO (set false to use externalMinio) |
| minio.mode | string | `"standalone"` | MinIO deployment mode |
| minio.rootUser | string | `"minioadmin"` | MinIO root username |
| minio.rootPassword | string | `"changeme"` | MinIO root password — REQUIRED: override in production |
| minio.persistence.enabled | bool | `true` | Enable persistent storage for MinIO |
| minio.persistence.size | string | `"20Gi"` | PVC size for MinIO data |
| minio.resources.requests.memory | string | `"512Mi"` | Memory request for MinIO |
| minio.resources.requests.cpu | string | `"250m"` | CPU request for MinIO |
| minio.resources.limits.memory | string | `"1Gi"` | Memory limit for MinIO |
| minio.resources.limits.cpu | string | `"500m"` | CPU limit for MinIO |
| minio.livenessProbe.enabled | bool | `true` |  |
| minio.livenessProbe.initialDelaySeconds | int | `30` |  |
| minio.readinessProbe.enabled | bool | `true` |  |
| minio.readinessProbe.initialDelaySeconds | int | `15` |  |
| valkey.enabled | bool | `true` | Deploy bundled Valkey (set false to use externalValkeyURL) |
| valkey.auth.enabled | bool | `false` | Enable ACL authentication for Valkey (false = no password required for in-cluster use) |
| valkey.resources.requests.cpu | string | `"100m"` | CPU request for Valkey |
| valkey.resources.requests.memory | string | `"128Mi"` | Memory request for Valkey |
| valkey.resources.limits.cpu | string | `"500m"` | CPU limit for Valkey |
| valkey.resources.limits.memory | string | `"256Mi"` | Memory limit for Valkey |
| valkey.dataStorage.enabled | bool | `true` | Enable persistent storage for Valkey |
| valkey.dataStorage.size | string | `"8Gi"` | PVC size for Valkey data |
| valkey.dataStorage.storageClass | string | `""` | StorageClass for Valkey PVC (empty = cluster default) |
