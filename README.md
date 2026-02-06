# Solotenmo

Solotenmo is a solo-built, full-stack money transfer application that demonstrates
secure API design, transactional business logic, and multi-client consumption of a backend service.

This project was developed to showcase backend ownership, authentication, persistence,
and realistic domain modeling around account balances and peer-to-peer transfers.

---

## Architecture Overview

Solotenmo follows a layered architecture with strict separation of concerns:

- **API Layer** – REST controllers expose authenticated endpoints
- **Service Layer** – Business rules and validation
- **DAO Layer** – JDBC-based persistence
- **Security Layer** – JWT authentication and authorization
- **Clients** – CLI and React clients consuming the same API

Client (CLI / React)
↓
REST Controllers
↓
Services
↓
DAOs
↓
PostgreSQL


---

## What Works Today

### Backend (tenmo-server)
- User registration and login
- JWT-based authentication
- Account and balance retrieval
- Peer-to-peer money transfers
- Transfer status and type management
- Transaction history per user
- Centralized exception handling
- Input validation and SQL injection checks
- Logging (info / warn / error)
- DAO integration tests

### Clients
- **CLI Client (`tenmo-client`)**
  - Authenticated login
  - Balance display
  - Create transfers
  - View transfer history
  - Approve / reject pending transfers

- **React Client (`tenmo-react-client`)**
  - Present but not fully integrated
  - Intended UI client for the same API

---

## Tech Stack

### Backend
- Java
- Spring-style REST architecture
- JDBC (DAO pattern)
- PostgreSQL
- JWT (stateless authentication)
- Maven

### Clients
- Java CLI client
- React (early-stage client)

---

## Repository Structure

Solotenmo/
├── database/
│ └── tenmo.sql
├── tenmo-server/
│ ├── controller/
│ ├── service/
│ ├── dao/
│ ├── security/
│ ├── model/
│ ├── util/
│ └── test/
├── tenmo-client/
│ ├── handler/
│ ├── services/
│ ├── model/
│ └── util/
└── tenmo-react-client/


---

## Database

- Relational schema defined in `database/tenmo.sql`
- Accounts, users, transfers, transfer types, and statuses
- Enforces referential integrity and balance correctness

---

## Security

- Stateless JWT authentication
- Authorization enforced at controller level
- Custom authentication entry points and filters
- Explicit rejection of unauthorized access
- Defensive input validation utilities

---

## Testing

- DAO-level integration tests
- Isolated test database configuration
- Seed data provided for repeatable test runs

---

## Current Limitations

- React client is incomplete
- No containerization (yet)
- No CI pipeline
- Manual startup steps
- Limited automated test coverage outside DAOs

---

## Roadmap

- [ ] Document exact startup steps (server + DB)
- [ ] Add Docker Compose for DB + API
- [ ] Finish React client integration
- [ ] Add service-layer tests
- [ ] Add CI workflow
- [ ] Add API documentation (OpenAPI)
- [ ] Improve error reporting to clients

---

## Portfolio Intent

This project exists to demonstrate:

- Solo backend ownership
- Secure, real-world domain modeling
- Clean layering and separation of concerns
- Practical authentication and authorization
- Transfer-safe transactional logic

It is intentionally kept as a realistic, non-trivial system rather than a polished demo.
