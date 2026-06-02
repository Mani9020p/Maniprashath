# MANIPRASHATH K S — DevOps Portfolio

> 🚀 A premium Linux Operations Center-themed portfolio built with Node.js, Express, MongoDB, and Docker.

[![CI/CD](https://github.com/Mani9020p/portfolio/actions/workflows/github-actions.yml/badge.svg)](https://github.com/Mani9020p/portfolio/actions)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?logo=docker)](./docker-compose.yml)
[![License](https://img.shields.io/badge/License-MIT-green)](./LICENSE)

---

## 🏗 Architecture

```
                        ┌──────────────────────────────────┐
                        │         Cloudflare CDN            │
                        └─────────────┬────────────────────┘
                                       │
                        ┌─────────────▼────────────────────┐
                        │          Nginx (SSL/TLS)          │
                        └──────┬──────────────┬────────────┘
                               │              │
              ┌────────────────▼──┐    ┌──────▼──────────────┐
              │  Frontend (Static HTML) │    │  Backend (Express)   │
              │   Port 80         │    │    Port 5000          │
              └───────────────────┘    └──────┬──────────────┘
                                               │
                                ┌──────────────▼──────────────┐
                                │      MongoDB (Port 27017)    │
                                └─────────────────────────────┘
```

---

## 🚀 Quick Start

### Prerequisites
- Docker 24+ & Docker Compose v2
- Node.js 20+
- Git

### 1. Clone
```bash
git clone https://github.com/Mani9020p/portfolio.git
cd portfolio
```

### 2. Configure environment
```bash
cp backend/.env.example backend/.env
# Edit backend/.env with your values
```

### 3. Run with Docker Compose
```bash
docker compose up -d
# Visit http://localhost:3000
```

### 4. Run locally (dev mode)
```bash
# Backend
cd backend && npm install && npm run dev

# Open index.html in browser for the static frontend
```

---

## 📁 Project Structure

```
portfolio/
├── index.html                    # Main portfolio (static)
├── docker-compose.yml            # Full stack orchestration
├── backend/
│   ├── server.js                 # Express app entry
│   ├── routes/                   # API route handlers
│   │   ├── auth.js               # JWT authentication
│   │   ├── projects.js           # Projects CRUD
│   │   ├── skills.js             # Skills CRUD
│   │   ├── certifications.js     # Certifications CRUD
│   │   ├── experience.js         # Experience CRUD
│   │   ├── education.js          # Education CRUD
│   │   ├── contact.js            # Contact form + email
│   │   ├── upload.js             # File uploads
│   │   └── analytics.js          # Page view tracking
│   ├── models/
│   │   └── index.js              # Mongoose schemas
│   ├── middleware/
│   │   └── auth.js               # JWT middleware
│   └── package.json
└── devops/
    ├── docker/
    │   └── Dockerfile.backend
    ├── nginx/
    │   └── nginx.conf            # Production Nginx config
    ├── k8s/
    │   └── manifests.yml         # K8s deployments + services
    ├── terraform/
    │   └── main.tf               # AWS infrastructure
    └── ci-cd/
        └── github-actions.yml    # CI/CD pipeline
```

---

## 🔐 Admin Panel

Access the admin panel at `/admin.html` (create separately or use API directly).

**Default credentials** (change immediately!):
- Username: `admin`
- Password: `changeme123`

Generate a bcrypt hash for production:
```bash
node -e "const b=require('bcryptjs'); console.log(b.hashSync('yourpassword', 10))"
```

---

## 📡 API Endpoints

| Method | Endpoint                    | Auth | Description           |
|--------|-----------------------------|------|-----------------------|
| POST   | /api/auth/login             | No   | Get JWT token         |
| POST   | /api/auth/verify            | No   | Verify token          |
| GET    | /api/projects               | No   | List projects         |
| POST   | /api/projects               | Yes  | Create project        |
| PUT    | /api/projects/:id           | Yes  | Update project        |
| DELETE | /api/projects/:id           | Yes  | Delete project        |
| GET    | /api/skills                 | No   | List skills           |
| POST   | /api/skills                 | Yes  | Create skill category |
| GET    | /api/certifications         | No   | List certifications   |
| GET    | /api/experience             | No   | List experience       |
| GET    | /api/education              | No   | List education        |
| POST   | /api/contact                | No   | Send contact message  |
| GET    | /api/contact                | Yes  | Admin: list messages  |
| POST   | /api/analytics/track        | No   | Track page view       |
| GET    | /api/analytics/summary      | Yes  | Admin: get analytics  |

---

## 🐳 Docker Commands

```bash
# Start all services
docker compose up -d

# View logs
docker compose logs -f backend

# Rebuild after changes
docker compose up -d --build

# Stop everything
docker compose down

# Clean up volumes (WARNING: deletes data)
docker compose down -v
```

---

## ☸️ Kubernetes Deployment

```bash
# Apply all manifests
kubectl apply -f devops/k8s/manifests.yml

# Check deployment status
kubectl get pods -n portfolio

# View logs
kubectl logs -f deployment/backend -n portfolio

# Scale backend
kubectl scale deployment/backend --replicas=3 -n portfolio
```

---

## 🏗 Terraform (AWS)

```bash
cd devops/terraform

# Initialize
terraform init

# Plan
terraform plan -out=tfplan

# Apply
terraform apply tfplan

# Destroy
terraform destroy
```

---

## 🔍 Environment Variables

| Variable       | Description                    | Default              |
|----------------|--------------------------------|----------------------|
| PORT           | Backend server port            | 5000                 |
| MONGO_URI      | MongoDB connection string      | mongodb://localhost   |
| JWT_SECRET     | JWT signing secret             | devops-secret        |
| ADMIN_USER     | Admin username                 | admin                |
| ADMIN_HASH     | Bcrypt hash of admin password  | —                    |
| EMAIL_USER     | Gmail account for notifications| —                    |
| EMAIL_PASS     | Gmail app password             | —                    |
| FRONTEND_URL   | Allowed CORS origin            | http://localhost:3000|

---

## 👤 About

**Maniprashath K S**
- 📧 maniprashathks@gmail.com
- 📱 +91 9788333773
- 🐙 [github.com/Mani9020p](https://github.com/Mani9020p)
- 🎓 BCA (DevOps & Automation) — Rathinam College of Arts & Science

---

## 📄 License

MIT License — see [LICENSE](./LICENSE) for details.
