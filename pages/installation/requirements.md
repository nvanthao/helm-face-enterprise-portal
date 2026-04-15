---
title: Embedded Cluster Installation Requirements
visible_when:
  entitlements:
    - isEmbeddedClusterDownloadEnabled
---

# HelmFace Embedded Cluster Installation Requirements

Ensure your environment meets these requirements before installing HelmFace via Embedded Cluster on Linux.

## System Requirements

- Linux operating system
- x86-64 architecture
- systemd
- At least 2GB of memory and 2 CPU cores
- Disk write latency: Maximum P99 write latency of 10ms (required for etcd performance)
- Root access or `sudo` privileges
- Data directory requirements:
  - 40Gi or more of total space
  - Less than 80% full
  - Default location: `/var/lib/embedded-cluster`
  - Can be changed with the `--data-dir` flag during installation

## Port Requirements

The following ports must be open and available for Embedded Cluster installations.

### Ports Used by Local Processes

These ports must be available for local processes (no firewall openings needed):

- 2379/TCP
- 7443/TCP
- 9099/TCP
- 10248/TCP
- 10257/TCP
- 10259/TCP

### Ports for Node Communication

These ports are used for bidirectional communication between nodes in multi-node installations. Create firewall openings between nodes for these ports:

- 2380/TCP — etcd cluster communication
- 4789/UDP — container networking
- 6443/TCP — Kubernetes API server
- 9091/TCP — metrics server
- 9443/TCP — Kubernetes webhook server
- 10249/TCP — kube-proxy metrics
- 10250/TCP — kubelet API
- 10256/TCP — kube-proxy health

### Admin Console Port

Port **30000/TCP** must be open and accessible for the Embedded Cluster Admin Console. This is where operators configure HelmFace settings, manage licenses, and check for updates. This port must also be accessible by nodes joining a multi-node cluster.

If port 30000 is occupied, you can select a different port during installation using the `--admin-console-port` flag.

### HelmFace Application Port

HelmFace application runs internally on port **3000** but is exposed via Traefik ingress. By default, it is accessible through:
- HTTP: Port **80** (redirect to HTTPS)
- HTTPS: Port **443** (main access)

If you need to avoid port collision with other services, you can modify the Traefik NodePort mappings via the Admin Console configuration screen.

### Local Artifact Mirror (LAM) Port

Port **50000/TCP** must be open for the Local Artifact Mirror (for container image distribution in air-gapped environments).

If port 50000 is occupied, you can select a different port during installation.

## Firewalld Configuration

If Firewalld is enabled in your environment, Embedded Cluster will automatically configure it to allow necessary traffic. No additional configuration is required.

The following ports are automatically opened in the default zone:

- 6443/TCP
- 10250/TCP
- 9443/TCP
- 2380/TCP
- 4789/UDP

## Additional System Directories

In addition to the primary data directory, Embedded Cluster creates files in these locations:

- `/etc/cni`
- `/etc/k0s`
- `/opt/cni`
- `/opt/containerd`
- `/run/calico`
- `/run/containerd`
- `/run/k0s`
- `/var/lib/calico`
- `/var/lib/cni`
- `/var/lib/containers`
- `/var/lib/kubelet`
- `/var/log/embedded-cluster`
- `/usr/local/bin/k0s`
