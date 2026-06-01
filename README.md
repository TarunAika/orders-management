# Orders Management System

An enterprise-grade Order Management System built on **MuleSoft Anypoint Platform** using API-led connectivity. The system is structured across three decoupled Mule applications — Experience, Process, and System — each handling a distinct layer of responsibility.

---

## Architecture

```
Client Request
     │
     ▼
┌─────────────────────┐
│   Experience API    │  ← Exposes REST endpoints, handles input validation
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│    Process API      │  ← Orchestrates business logic, inventory checks
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│     System API      │  ← Interfaces with the database (MySQL)
└─────────────────────┘
```

---

## Features

- Bulk order processing with input validation
- Inventory checks before order confirmation
- Item-level error handling — a single bad item doesn't fail the entire batch
- Modular RAML 1.0 specs with reusable data types, traits, and libraries published to Anypoint Exchange
- Client ID Enforcement via API Manager
- Deployed on CloudHub 2.0 across Dev, Test, and SIT environments

---

## Tech Stack

| Layer | Technology |
|---|---|
| Integration Platform | MuleSoft Anypoint Studio |
| Transformation | DataWeave 2.0 |
| API Spec | RAML 1.0 |
| API Publishing | Anypoint Exchange |
| Deployment | CloudHub 2.0 |
| Database | MySQL |
| Testing | Postman |

---

## Project Structure

```
orders-management/
├── order-management-exp-api/        # Experience layer — client-facing endpoints
├── order-management-process-api/    # Process layer — business logic & orchestration
└── order-management-sys-api/        # System layer — database operations
```

---

## Getting Started

### Prerequisites

- Anypoint Studio 7.x
- MuleSoft Runtime 4.x
- MySQL database
- Postman (for testing)

### Setup

1. Clone the repository
   ```bash
   git clone https://github.com/TarunAika/orders-management.git
   ```

2. Open each project folder in Anypoint Studio as a separate Mule project

3. Copy `dev.yaml.example` to `dev.yaml` in each project and fill in your credentials
   ```
   src/main/resources/dev.yaml
   ```

4. Run each Mule application individually starting from System → Process → Experience

5. Test the endpoints using Postman

---

## Environments

| Environment | Purpose |
|---|---|
| Dev | Local development |
| Test | Integration testing |
| SIT | System integration testing |

---

## API Policies

- **Client ID Enforcement** applied via Anypoint API Manager on all endpoints
- All APIs published and versioned on **Anypoint Exchange**