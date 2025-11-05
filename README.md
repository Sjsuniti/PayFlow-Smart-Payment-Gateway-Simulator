# PayFlow – Smart Payment Gateway Simulator  
> A backend-heavy payment orchestration simulator (UPI / Card / Wallet) with smart routing, retries, circuit breakers & analytics dashboard.

---

## 🚀 Overview
PayFlow is a **payment gateway simulator** designed to mimic real payment orchestration systems like Razorpay, Stripe, Juspay, and VisaNet.  
It supports:
- Multi-provider routing
- Intelligent retries
- Failure handling
- Circuit-breaker logic
- JSON-based provider configuration
- Transaction simulation
- Real-time analytics dashboard

This project is built to deepen understanding of **system design, reliability, backend engineering, and payments domain concepts**.

---

PayFlow simulates such real-world behavior and helps demonstrate practical skills required for backend roles in **Google | Visa | Juspay | Razorpay | PayTM | Stripe-like companies**.

---

## ✨ Features (Planned & Completed)

| Feature | Status |
|--------|--------|
| Basic Express server | ✅ |
| MongoDB models | ✅ |
| Create payment API (PENDING) | 🔄 |
| Idempotency support | 🔄 |
| Provider adapters (UPI/Card/Wallet) | 🔄 |
| Provider config via JSON | 🔄 |
| Retry strategy | 🔄 |
| Failover + Backup Routing | 🔄 |
| Circuit breaker | 🔄 |
| Queue + Worker (BullMQ) | 🔄 |
| Webhooks with HMAC signature | 🔄 |
| Reconciliation service | 🔄 |
| Dashboard (React) | 🔄 |
| Metrics (Prometheus / OTEL) | 🔄 |
| Seed + 10K mock transactions | 🔄 |
| Load testing (k6) | 🔄 |
| Anomaly alerts | 🔄 |
| Double-entry Ledger | 🔄 |
| Multi-tenant merchants | 🔄 |

---

## 🧠 Architecture

### High-Level 




### Components
- **API Layer** — Input validation + idempotency
- **Router** — Chooses best provider based on config + health
- **Worker** — Processes payments & retries
- **Provider Adapter** — Standard interface for all payment providers
- **Reconciliation job** — Fix mismatches
- **Dashboard** — Metrics visualization
- **DB Layer** — MongoDB (Payments + Ledger)
- **Cache/Queue** — Redis + BullMQ

---

## 🏗 Tech Stack

### Backend
- Node.js
- Express
- TypeScript
- MongoDB
- Redis
- BullMQ (Queues / Retries)
- Zod (Validation)
- OpenTelemetry (Traces)
- Prometheus / Grafana (Metrics)
- Pino (Logging)

### Frontend
- React
- Vite
- Shadcn/UI or MUI
- Recharts
- TanStack Query

---

## 📁 Folder Structure (Planned)

payflow/
│
├── apps/
│ ├── api/ # Express API
│ ├── worker/ # Queue processors
│ └── dashboard/ # React UI
│
├── packages/
│ ├── providers/ # Provider adapters
│ ├── routing/ # Routing logic
│ └── core/ # Types + utils
│
├── infra/
│ ├── docker-compose.yml # Mongo + Redis + Grafana
│ └── k6/ # Load tests
│
├── scripts/
│ ├── seed.ts # Generate mock transactions
│
├── docs/
│ ├── architecture.md
│ ├── api.md
│ ├── sla.md
│ └── reconciliation.md
│
└── README.md


---

## 🔌 API (Initial Plan)

| Method | Endpoint | Purpose |
|--------|----------|---------|
| POST   | `/api/v1/payments` | Create new payment (idempotent) |
| GET    | `/api/v1/payments/:txnId` | Fetch payment details |
| POST   | `/api/v1/payments/:txnId/refund` | Refund |
| GET    | `/api/v1/analytics` | Dashboard stats |
| GET    | `/internal/metrics` | Prometheus |

---

## 🔧 Setup (Planned)

```bash
git clone https://github.com/<yourname>/payflow
cd payflow
pnpm install
docker compose up -d
pnpm dev
🧩 Provider Config Example
providers.json

json
Copy code
[
  {
    "id": "mockCardA",
    "type": "CARD",
    "timeoutMs": 1200,
    "failureRate": 0.05,
    "latencyMs": { "min": 150, "max": 800 },
    "routingRules": {
      "bins": ["51*", "52*"],
      "maxAmount": 500000
    }
  }
]
```
📊 Dashboard Features
Provider success / failure
Latency histograms
Failure spike alerts
Circuit-breaker status
Routing health
Transaction detail drilled view

⚙️ Future Enhancements
Risk engine
A/B routing
Wallet balance simulation
Multi-currency FX
Plugin marketplace
Tokenization simulation


📌 Status
Work In Progress 

