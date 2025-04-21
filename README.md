# 🛰️ THOC - Trusted Hyper Orchestrator for Cloud

**THOC** is an on-premise cloud platform that provides flexible virtualization infrastructure provisioning services, including virtual machines, networking, storage, orchestration, and workloads. The system is divided into independent, easily scalable, and maintainable modules.

---

## 🧱 Kiến trúc Dịch vụ

### 0. Infrastructure
Chứa các thành phần hạ tầng cốt lõi:
- **Database**: Schema, migration tool, seed data
- **Queue**: RabbitMQ/Kafka cấu hình hàng đợi và consumer
- **Cache**: Redis cấu hình key TTL và prefix
- **Logging / Tracing / Metrics**: Hệ thống log tập trung, OpenTelemetry, Prometheus rule

---

### 1. Identity
- Quản lý người dùng, domain, policy, phân quyền (RBAC)
- OAuth2 / JWT / Token
- Tích hợp LDAP (nếu cần)

---

### 2. Dashboard
- Giao diện web quản lý tài nguyên
- Gọi API từ các mô-đun backend
- Quản lý project, quota, lifecycle tài nguyên

---

### 3. Monitoring
- Quan sát hệ thống (Grafana, Prometheus, AlertManager)
- Tích hợp với hệ thống log (EFK stack, Loki)

---

### 4. Compute
- THOC Compute Service (tương đương OpenStack Nova)
- Quản lý VM lifecycle (start/stop/reboot/delete)
- Scheduler đa node libvirt backend
- Tích hợp noVNC console, serial proxy

---

### 5. Network
- Quản lý mạng ảo (VLAN/VXLAN, IPAM)
- Giao tiếp layer 2/3 giữa các instance
- DHCP, DNS, NAT, Floating IP

---

### 6. Storage
- Quản lý block storage (THOC Block)
- Hỗ trợ nhiều backend: Ceph, GlusterFS, NFS
- Snapshot, volume attach/detach

---

### 7. Orchestration
- Quản lý template, autoscaling, lifecycle resource
- Tích hợp Workflow Engine (Argo Workflows, Temporal)

---

### 8. WorkLoadEngine
- Cung cấp Kubernetes-as-a-Service
- Quản lý cluster, node pool, registry tích hợp

---

## 🚀 Hướng phát triển tiếp theo

- [ ] Multi-tenant
- [ ] Billing module
- [ ] Plugin hệ thống AI Assistant
- [ ] Federation hỗ trợ nhiều datacenter

---

## 📁 Cấu trúc thư mục

```bash
THOC/
├── 0.Infrastructure/
│   ├── Database/
│   ├── Queue/
│   ├── Cache/
│   ├── Logging/
│   └── Tracing/
├── 1.Identity/
├── 2.Dashboard/
├── 3.Monitoring/
├── 4.Compute/
├── 5.Network/
├── 6.Storage/
├── 7.Orchestration/
└── 8.WorkLoadEngine/
