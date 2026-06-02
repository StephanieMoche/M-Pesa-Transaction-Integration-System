# M-Pesa Transaction Integration System
Project Status: In active development.

A Spring Boot-based payment processing system inspired by M-Pesa transaction workflows. This project simulates core digital wallet operations, including deposits, withdrawals, wallet-to-wallet transfers, transaction history tracking, and callback handling.

The goal of this project is to explore how modern fintech payment systems are designed, built, and maintained while focusing on transactional consistency, API design, and backend engineering best practices.

---

## Features

### Wallet Management

* Create and manage customer wallets
* Retrieve wallet information
* Check wallet balances

### Transaction Processing

* Deposit funds
* Withdraw funds
* Wallet-to-wallet transfers
* Transaction history tracking
* Transaction status management

### Reliability & Security

* Input validation
* Global exception handling
* Transactional consistency using Spring Transactions
* Structured logging
* Secure API design principles

### Callback Processing

* Simulated M-Pesa callback handling
* Transaction status updates
* Event tracking and auditing

---

## Tech Stack

* Java
* Spring Boot
* Spring Data JPA
* PostgreSQL
* Maven
* REST APIs
* Git

---

## Project Structure

```text
src/main/java/com/mpesa

├── wallet
│   ├── controller
│   ├── service
│   ├── repository
│   ├── dto
│   └── entity
│
├── transaction
│   ├── controller
│   ├── service
│   ├── repository
│   ├── dto
│   └── entity
│
├── callback
│   ├── controller
│   └── service
│
└── common
    ├── exception
    ├── config
    ├── util
    └── enums
```

---

## Core Transaction Flow

### Transfer Money

1. User initiates a transfer request.
2. System validates the request.
3. Transaction record is created.
4. Sender wallet is debited.
5. Receiver wallet is credited.
6. Transaction status is updated.
7. Audit information is recorded.

All balance updates are performed within a database transaction to ensure consistency and prevent partial updates.

---

## API Endpoints

### Wallets

```http
POST /api/wallets
GET /api/wallets/{id}
GET /api/wallets/{id}/balance
```

### Transactions

```http
POST /api/transactions/deposit
POST /api/transactions/withdraw
POST /api/transactions/transfer
GET /api/transactions/{reference}
GET /api/transactions/history/{walletId}
```

### Callbacks

```http
POST /api/callbacks/mpesa
```

---

## Example Transfer Request

```json
{
  "senderPhone": "254700000001",
  "receiverPhone": "254700000002",
  "amount": 500
}
```

---

## Database Design

### Wallet

| Field       | Description              |
| ----------- | ------------------------ |
| id          | Unique wallet identifier |
| customerId  | Customer reference       |
| phoneNumber | Associated phone number  |
| balance     | Current wallet balance   |
| status      | Wallet status            |
| createdAt   | Creation timestamp       |

### Transaction

| Field            | Description                   |
| ---------------- | ----------------------------- |
| id               | Unique transaction identifier |
| reference        | Transaction reference         |
| senderWalletId   | Source wallet                 |
| receiverWalletId | Destination wallet            |
| amount           | Transaction amount            |
| type             | Deposit, Withdrawal, Transfer |
| status           | Pending, Success, Failed      |
| createdAt        | Creation timestamp            |

---

## Planned Enhancements

* JWT Authentication & Authorization
* Docker Containerization
* Kafka-based Event Processing
* Transaction Idempotency
* Rate Limiting
* Monitoring & Observability
* Cloud Deployment
* API Documentation with Swagger/OpenAPI

---

## Learning Objectives

I'm doing this project to deepen my understanding of:

* Backend Engineering
* Payment Processing Systems
* REST API Design
* Transaction Management
* Database Modeling
* Fintech Architecture
* Scalable System Design

---
