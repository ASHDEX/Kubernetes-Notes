# Kubernetes Notes

Architecture and security reference notes for Kubernetes, covering cluster hardening, RBAC, workload isolation, network policies, and audit logging for secure production deployments.

## Topics Covered

### Cluster Architecture

- Control plane components: API server, etcd, scheduler, controller manager
- Node components: kubelet, kube-proxy, container runtime
- Cluster networking model and CNI plugins (Calico, Cilium, Flannel)
- etcd encryption at rest and access control

### Security Hardening

| Area | Controls |
|---|---|
| API Server | Anonymous auth disabled, audit logging enabled, admission controllers |
| RBAC | Least-privilege roles, ServiceAccount token management, binding scope |
| Network Policies | Default-deny ingress/egress, namespace isolation, pod-level rules |
| Pod Security | SecurityContext, runAsNonRoot, readOnlyRootFilesystem, allowPrivilegeEscalation: false |
| Secrets | External secret operators (Vault, AWS Secrets Manager), encrypted etcd |
| Image Security | Signed images, admission webhooks (OPA Gatekeeper, Kyverno), registry policies |

### RBAC

- ClusterRole vs Role scope
- ServiceAccount binding and token projection
- Audit logging for privilege escalation patterns
- Common misconfigurations: wildcard verbs, cluster-admin binding

### Workload Isolation

- Namespace segmentation strategy
- Pod Security Standards (restricted, baseline, privileged)
- OPA / Gatekeeper policy enforcement
- Runtime security: Falco rules for anomaly detection

### Monitoring and Audit

- kube-apiserver audit policy configuration
- Audit log ingestion into SIEM (Sentinel, Splunk, Elastic)
- Falco rules for container escape, privilege escalation, network anomalies
- CIS Kubernetes Benchmark alignment

## Security Use Cases

- Reviewing cluster configurations against CIS Kubernetes Benchmark
- Identifying over-privileged ServiceAccounts and ClusterRoleBindings
- Writing Falco rules for container escape and lateral movement detection
- Assessing network policy coverage for east-west traffic control

## Author

ASHDEX — Security Researcher & Architect
[ashdex.com](https://ashdex.com)
