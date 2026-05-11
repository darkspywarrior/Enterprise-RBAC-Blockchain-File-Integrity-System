# 🔐 Enterprise RBAC Blockchain File Integrity System

> Production-style Role-Based Access Control (RBAC) File Integrity Verification Platform built using Hyperledger Fabric, Spring Boot, MinIO, Docker, Prometheus, Grafana, and NGINX.

---

# 🚀 Overview

This project is an enterprise-grade blockchain-powered file integrity and verification system implementing:

- 🔐 Role-Based Access Control (RBAC)
- 📦 Hyperledger Fabric Blockchain
- 🧾 Immutable Audit Trails
- ☁️ MinIO Object Storage
- ⚡ Spring Boot Microservices
- 📊 Prometheus Monitoring
- 📈 Grafana Dashboards
- 🐳 Docker Multi-Container Architecture
- 🌐 NGINX Reverse Proxy
- 📘 Swagger API Documentation

The system securely stores file fingerprints (SHA-256 hashes) on blockchain while storing actual file binaries in MinIO object storage.

This enables:

✅ Tamper Detection  
✅ Immutable Verification  
✅ Distributed Trust  
✅ Secure Off-Chain Storage  
✅ Enterprise Monitoring & Observability  

---

# 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │     Client Layer     │
                    │  Browser / Postman   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   NGINX Reverse Proxy │
                    │     TLS / Routing     │
                    └──────────┬───────────┘
                               │
        ┌──────────────────────┼──────────────────────┐
        ▼                                              ▼

┌──────────────────────┐                 ┌──────────────────────┐
│ Spring Boot API      │                 │ RBAC Authorization   │
│ File Upload Service  │                 │ Access Validation    │
└──────────┬───────────┘                 └──────────────────────┘
           │
           ▼

┌─────────────────────────────────────────────────────────────┐
│                    SHA-256 HASHING                         │
│      Generate Cryptographic File Fingerprints              │
└──────────────────────┬──────────────────────────────────────┘
                       │
          ┌────────────┴────────────┐
          ▼                         ▼

┌──────────────────────┐   ┌──────────────────────────────┐
│      MinIO Storage   │   │ Hyperledger Fabric Blockchain │
│  Binary Object Store │   │ Immutable Ledger + Chaincode │
└──────────────────────┘   └──────────────────────────────┘
                                         │
                                         ▼
                           ┌──────────────────────────┐
                           │  Org1 + Org2 Peers      │
                           │  RAFT Ordering Service  │
                           └──────────────────────────┘


┌─────────────────────────────────────────────────────────────┐
│                   Monitoring Stack                         │
│        Prometheus + Grafana + Actuator                    │
└─────────────────────────────────────────────────────────────┘
```
# ✨ Core Features

## 🔐 Blockchain File Integrity

- SHA-256 file fingerprint generation
- Immutable blockchain storage
- Tamper detection
- File integrity verification workflows

---

## 🛡 RBAC (Role-Based Access Control)

Supports multiple user roles:

| Role | Access |
|---|---|
| Admin | Full system access |
| Auditor | Audit trail verification |
| User | Upload & verify files |
| Viewer | Read-only access |

---

## 📦 Hybrid Storage Architecture

### On-Chain Storage

Stores:

- SHA-256 hashes
- file metadata
- timestamps
- ownership records

### Off-Chain Storage

Stores:

- actual file binaries
- PDFs
- images
- documents

using MinIO object storage.

---

## 📘 Swagger API Documentation

Interactive REST API testing interface.

Supports:

- upload APIs
- verification APIs
- audit APIs
- RBAC testing

---

## 📊 Monitoring & Observability

Integrated:

- Prometheus metrics
- Grafana dashboards
- JVM monitoring
- blockchain transaction tracking

---

# 📦 Technology Stack

| Technology | Purpose |
|---|---|
| Java 17 | Backend Runtime |
| Spring Boot | REST APIs |
| Hyperledger Fabric | Enterprise Blockchain |
| MinIO | Object Storage |
| Docker | Containerization |
| Docker Compose | Multi-container orchestration |
| Prometheus | Metrics collection |
| Grafana | Visualization dashboards |
| NGINX | Reverse proxy |
| Swagger/OpenAPI | API documentation |
| SHA-256 | Cryptographic hashing |
| RAFT | Consensus algorithm |

---

# 🔗 API Endpoints

## File APIs

| Method | Endpoint | Description |
|---|---|---|
| POST | `/file/upload` | Upload file to blockchain |
| POST | `/file/verify` | Verify file integrity |
| POST | `/file/upload-and-verify` | Upload + verify |
| GET | `/file/hash` | Current stored hash |
| DELETE | `/file/clear` | Clear temporary state |

---

## Blockchain APIs

| Method | Endpoint | Description |
|---|---|---|
| GET | `/audit/trail` | View blockchain records |
| GET | `/fabric/status` | Fabric network status |

---

## Monitoring APIs

| Method | Endpoint | Description |
|---|---|---|
| GET | `/actuator/prometheus` | Prometheus metrics |
| GET | `/swagger-ui/index.html` | Swagger UI |

---

# 🔐 Security Features

## SHA-256 Integrity Verification

Every uploaded file generates a cryptographic SHA-256 fingerprint.

Even a 1-bit modification changes the entire hash.

---

## TLS Encryption

All Fabric peer communications use:

- TLS certificates
- secure gRPC channels
- encrypted communication

---

## Immutable Ledger

Blockchain ensures:

- append-only transactions
- tamper resistance
- decentralized trust

---

## RBAC Authorization

Users are restricted based on roles and permissions.

---

## Input Validation

- file size restrictions
- file type validation
- invalid request filtering

---

# 📊 Monitoring Dashboard

## Prometheus Metrics

Tracked metrics include:

| Metric | Description |
|---|---|
| `file_uploads_total` | Total uploads |
| `fabric_transactions_total` | Blockchain transactions |
| `process_cpu_usage` | CPU monitoring |
| `jvm_memory_used_bytes` | JVM memory |
| `http_server_requests_seconds` | API latency |
| `minio_objects_total` | MinIO object count |

---

## Grafana Dashboard

Real-time dashboards for:

- blockchain health
- upload statistics
- transaction monitoring
- CPU / memory graphs
- API response metrics

---

# 📁 Project Structure

```text
Enterprise-RBAC-Blockchain-System
│
├── fingerprint-service
│   ├── src
│   ├── Dockerfile
│   ├── pom.xml
│   ├── wallet
│   └── fabric-config
│
├── blockchain
│   └── fabric
│       └── fabric-samples
│
├── prometheus
│   └── prometheus.yml
│
├── nginx
│   └── nginx.conf
│
├── docker-compose.yml
├── README.md
└── .env
