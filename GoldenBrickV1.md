# 🧱 The Golden Brick - System Design Checklist (v1.0)

## 🔍 Requirements Summary
- [x] Core Functional Requirement: e.g., user registration, login
- [x] Non-Functional Requirement: e.g., high availability, low latency

---

## 🌐 API Design
- Type & Why:
  - [x] RESTful ✅ — Easy integration with clients, stateless, cacheable
  - [ ] GraphQL 🟥 — Overkill for current scope, no nested data needs

---

## 📦 Backend Architecture
- [x] Framework/Language: Spring Boot (Java) ✅ — Mature, proven in prod
- [x] Design Patterns Used: MVC, Repository ✅

---

## 🛢️ Database Layer
- [x] Type:
  - PostgreSQL ✅ — ACID-compliant, supports JSON, suits relational needs
  - Redis ✅ — Used for caching user sessions
- [x] Sharding/Replication Needed? 🟥 No, scale is manageable for now

---

## 🚦Load Balancer
- Type & Why:
  - [x] Round Robin ✅ — Simple and effective for stateless services
  - [ ] Least Connections 🟥 — Not required at current traffic

---

## 🔄 Scaling Strategy
- [x] Horizontal Scaling ✅ — Using Docker Swarm/Kubernetes nodes
- [ ] Vertical Scaling 🟥 — Not scalable long-term, avoided

---

## 🚫 Single Point of Failure
- [x] Web Server Redundancy ✅ — Nginx on 2 nodes
- [x] DB Replica ✅ — Read replicas added
- [ ] External Dependency Redundancy 🟥 — Needs improvement

---

## 🔐 Security Measures
- [x] HTTPS enabled ✅
- [x] Input validation (backend & frontend) ✅
- [x] Authentication:
  - [x] JWT ✅ — Stateless & secure
- [x] Authorization checks ✅
- [x] Firewall Rules ✅ — Only 80/443/22 open

---

## 🧰 DevOps/Infra Setup
- [x] Dockerized ✅
- [x] Docker Compose (Dev) ✅
- [x] Kubernetes (Prod) 🟥 — Not yet, maybe phase 2
- [x] CI/CD: Jenkins or GitHub Actions ✅
- [x] Monitoring:
  - Prometheus + Grafana ✅
- [x] Logging:
  - ELK stack ✅

---

## 📈 Metrics to Watch
- [x] API latency
- [x] Error rates (4xx/5xx)
- [x] DB response time
- [x] CPU/Memory usage

---

## 📋 Testing
- [x] Unit Tests ✅
- [x] Integration Tests ✅
- [x] Load Testing 🟥 (Planned with k6)

---

## 📦 Deployment
- [x] Environments: Dev ✅ | Stage ✅ | Prod ✅
- [x] Zero Downtime ✅
- [x] Rollback Strategy ✅

---

## 📅 Maintenance Plan
- [x] Backup Schedule ✅ (Daily snapshots)
- [x] Log Rotation ✅
- [x] Dependency Updates ✅

---

## 📚 Documentation
- [x] README.md ✅
- [x] API Swagger/OpenAPI ✅
- [x] Infrastructure-as-Code notes ✅ (Ansible or Terraform)

---

## 🧠 Lessons Learned (Post-Mortem / Retro)
> Keep a section here for notes on what went well, what didn’t, and what would you change.

---

# 🧱 End of Golden Brick
