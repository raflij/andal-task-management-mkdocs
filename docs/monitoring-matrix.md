# Monitoring & Alerting Matrix

*Last Updated: September 10, 2025*

## Environment-based Alert Configuration

| Alert | Component | Dev Feature | Dev Stable | Testing | Staging | Performance | Production | Prod Replica |
|-------|-----------|-------------|------------|---------|---------|-------------|------------|--------------|
| **Bare Metal / VM** | CPU | | | ✅  | ✅  | ✅  | ✅  | |
| | Memory | | | ✅  | ✅  | ✅  | ✅  | |
| | Storage Mesin | | | ✅  | ✅  | ✅  | ✅  | |
| | Node Mati | ✅  | ✅  | ✅  | ✅  | ✅  | ✅  | |
| | CPU load | | | | | | | |
| | per-core usage | | | | | | | |
| | interrupt rate | | | | | | | |
| | iowait | | | | | | | |
| | disk utilization (bytes and inodes) | | | | | | | |
| | disk latency (await) | | | | | | | |
| | iops | | | | | | | |
| | syslog | | | | | | | |
| | dmesg | | | | | | | |
| | kernel OOM | | | | | | | |
| | disk errors | | | | | | | |
| | Rising iowait with high disk latency | | | | | | | |
| | filesystem read/write errors | | | | | | | |
| | CRC/packet drops | | | | | | | |
| | Unexpected instance termination / reboots / host unreachable | | | | | | | |
| **K8S Cluster** | CPU | | | ✅  | ✅  | ✅  | ✅  | |
| | Memory | | | ✅  | ✅  | ✅  | ✅  | |
| | Klaster Down / Node Ready=false | | | ✅  | ✅  | ✅  | ✅  | ✅  |
| | Block Storage | | | | | ✅  | ✅  | |
| | Pod Crash | | | | | | | |
| | Pod Down | | | | | | | |
| | PVC Health | | | | | | | |
| | Orchestrator 2/2 | | | ✅  | ✅  | | ✅  | |
| | Kubeconfig will expired | | | | | | | |
| | APIserver metrics: request latencies (p999/p95), error rates (5xx), authentication errors | | | | | | | |
| | etcd metrics: leader changes, commit duration, operation latency, database size, disk fsync latency, number of proposals/failed proposals | | | | | | | |
| | Scheduler metrics: scheduling latency, failed scheduling events, pending pods count | | | | | | | |
| | Controller-manager: reconcile errors, crashloops | | | | | | | |
| | Audit logs, apiserver logs, kube-apiserver restarts | | | | | | | |
| | APIserver latency > 1s for control operations or 5xx errors → cluster unreliable | | | | | | | |
| | Etcd leader flapping or high commit latency → data store instability / risk of data loss | | | | | | | |
| | Many pods in Pending due to scheduling or volume binding timeouts | | | | | | | |
| | kubelet health | | | | | | | |
| | kubelet errors | | | | | | | |
| | CRI errors | | | | | | | |
| | container_image_pull_failures | | | | | | | |
| | kube_pod_container_status_restarts_total | | | | | | | |
| | oom_kill events | | | | | | | |
| | Frequent kubelet restarts or container runtime (CRI) errors | | | | | | | |
| | CrashLoopBackOff spikes / containers restarted many times | | | | | | | |
| **API & Ingress Layer** | Request rates | | | | | | | |
| | 5xx/4xx rates | | | | | | | |
| | latencies (p50/p95/p99) | | | | | | | |
| | TLS handshake errors | | | | | | | |
| | dropped or rate-limited requests | | | | | | | |
| | Ingress controller logs | | | | | | | |
| | config errors (invalid routes) | | | | | | | |
| | Increased 5xx rate | | | | | | | |
| | error ratio crossing SLO | | | | | | | |
| | TLS certificate expiring or handshake failures | | | | | | | |
| | Rate-limit spikes indicating DoS | | | | | | | |
| **Ceph Cluster** | OSD Mati | | | | | | | |
| | OSD Usage | | | | | | | |
| **Microservices Logs** | All Microservices | | | | | | | |
| **Storage Apps** | Citus | | | ✅  | ✅  | | | |
| | Kafka | | | | | | | |
| | Redis Microservices | | | ✅  | ✅  | | | |
| | Redis Dapr | | | ✅  | ✅  | | | |
| | Keycloak Patroni | | | | | | | |
| | Vcluster | | | | | | | |
| | Static App | | | | | | | |
| **3rd party App down** | DB Down / Crash | | | | | | | |
| | Redis Down / Crash | | | | | | | |
| | Keycloak Down / Crash | | | | | | | |
| | Debezium Down / Crash | | | | | | | |
| | Kafka Down / Crash | | | | | | | |
| | Flow CDC Down | | | | | | | |
| | Minio Down / Crash | | | | | | | |
| **Storage (PV/PVC/CSI/RBD/Ceph/MinIO)** | PV capacity | | | | | | | |
| | PVC usage | | | | | | | |
| | storage latency (read/write latencies) | | | | | | | |
| | IO errors | | | | | ✅  | ✅  | |
| | CSI controller logs | | | | | ✅  | ✅  | |
| | Inode usage | | | ✅  | ✅  | | ✅  | |
| | filesystem remounts/read-only events | | | | | | | |
| | PVC near-full or PV read-only or FailedAttachVolume | | | | | | | |
| | High storage latency causing app timeouts | | | | | | | |
| **Networking** | CoreDNS latency/errors | | | | | | | |
| | DNS error rates | | | | | | | |
| | CNI plugin logs | | | | | | | |
| | Service endpoints missing | | | | | | | |
| | iptables or IPVS errors | | | | | | | |
| | Network packet loss | | | | | | | |
| | retransmits | | | | | | | |
| | connection resets | | | | | | | |
| | socket exhaustion | | | | | | | |
| | DNS lookup latencies or NXDOMAIN spikes leading to app timeouts | | | | | | | |
| | Service endpoints mismatch (service has no endpoints) | | | | | | | |
| | LoadBalancer health check failing for backend pods (traffic blackhole) | | | | | | | |
| | Nodeport/ingress rules incorrect or failing | | | | | | | |
| **Keycloak** | response latency | | | | | | | |
| | 5xx rate | | | | | | | |
| | DB errors | | | | | | | |
| | login failures | | | | | | | |
| | user lockouts | | | | | | | |
| | DB connectivity errors | | | | | | | |
| **Redis / Redis Dapr / Cache** | memory usage | | | | | | | |
| | eviction rate | | | | | | | |
| | ops/sec | | | | | | | |
| | latency | | | | | | | |
| | connected clients | | | | | | | |
| | persistence RDB/AOF errors | | | | | | | |
| | replication lag | | | | | | | |
| | role changes | | | | | | | |
| | eviction spikes (cache thrash) | | | | | | | |
| | increased latency | | | | | | | |
| | replication broken | | | | | | | |
| | persistence failing | | | | | | | |
| **Kafka** | broker CPU/io | | | | | | | |
| | request latency | | | | | | | |
| | under-replicated partitions (URP) | | | | | | | |
| | offline partitions | | | | | | | |
| | consumer group lag | | | | | | | |
| | partition leader changes | | | | | | | |
| | URP > 0 | | | | | | | |
| | controller changes flapping | | | | | | | |
| | consumer lag growing | | | | | | | |
| **Citus** | replication lag | | | | | | | |
| | CPU | | | | | | | |
| | active connections | | | | | | | |
| | slow queries | | | | | | | |
| | lock waits | | | | | | | |
| | replication slots | | | | | | | |
| | disk usage | | | ✅  | | | | |
| | checkpoint duration | | | | | | | |
| | long-running queries | | | | | | | |
| | high lock contention | | | | | | | |
| | replication lag | | | | | | | |
| | connection pool exhaustion | | | | | | | |
| **Debezium / CDC** | connector status | | | ✅  | ✅  | | ✅  | |
| | last processed offset | | | | | | | |
| | lag | | | | | | | |
| | error logs | | | | | | | |
| | connector stopped | | | | | | | |
| | offset not progressing | | | | | | | |
| | repeated errors | | | | | | | |
| **Dapr** | sidecar health | | | | | | | |
| | component binding errors | | | | | | | |
| | actor failures | | | | | | | |
| | sidecar down for an app | | | | | | | |
| **MinIO / Object Store** | disk usage | | | | | | | |
| | object put/get latency and error rates | | | | | | | |
| | replication/erasure coding errors | | | | | | | |
| | access denied spikes | | | | | | | |
| | mounts read-only | | | | | | | |
| | object-store errors on PUT/GET | | | | | | | |
| **Pods & Application Health** | Readiness & liveness probe failures | | | | | | | |
| | restarts | | | | | | | |
| | OOMs | | | | | | | |
| | CPU throttling | | | | | | | |
| | thread pool exhaustion | | | | | | | |
| | request error rates | | | | | | | |
| | SLO violation rates | | | | | | | |
| | p95/p99 latencies | | | | | | | |
| | application logs with errors/exceptions | | | | | | | |
| | Readiness probe failing (app not receiving traffic) or liveness failing (CrashLoop) | | | | | | | |
| | App returning 200 but with error payloads (need application-level health checks) | | | | | | | |
| | High latency or error rate for key transactions even if CPU/memory is fine | | | | | | | |
| **Data Integrity & Consistency** | Consumer group lags | | | | | | | |
| | replication lag | | | | | | | |
| | read-your-write corrections | | | | | | | |
| | orphaned locks | | | | | | | |
| | missing messages | | | | | | | |
| | audit traces that check consistent flows | | | | | | | |
| | Replication divergence (Citus shards inconsistent) | | | | | | | |
| | Silent data loss: message acknowledged but not processed downstream, connectors not committing offsets, partial writes | | | | | | | |

## Alert Rules

Add your specific alert rules and thresholds here.

## Alert Routing

Define how alerts should be routed based on severity and environment.