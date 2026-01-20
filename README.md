<div align="center">

# 🏥 Patient Management System

### *Enterprise-Grade Microservices Architecture*

[![Java](https://img.shields.io/badge/Java-25-orange?style=for-the-badge&logo=java)](https://www.java.com)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.0+-brightgreen?style=for-the-badge&logo=spring)](https://spring.io/projects/spring-boot)
[![Kafka](https://img.shields.io/badge/Apache%20Kafka-Event%20Streaming-black?style=for-the-badge&logo=apache-kafka)](https://kafka.apache.org)
[![gRPC](https://img.shields.io/badge/gRPC-High%20Performance-blue?style=for-the-badge&logo=grpc)](https://grpc.io)
[![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?style=for-the-badge&logo=docker)](https://www.docker.com)

*A sophisticated healthcare backend system demonstrating modern distributed architecture patterns, event-driven design, and high-performance inter-service communication.*

[Features](#-features) • [Architecture](#-architecture) • [Quick Start](#-quick-start) • [API Docs](#-api-documentation) • [Contributing](#-contributing)

</div>

---

## 🎯 Features

<table>
<tr>
<td width="50%">

### 🔧 **Technical Excellence**
- ⚡ **High-Performance gRPC** communication
- 📨 **Event-Driven** architecture with Kafka
- 🔐 **JWT-based** secure authentication
- 🐳 **Fully Containerized** with Docker
- 🎯 **RESTful APIs** with Spring Cloud Gateway
- 💾 **JPA/Hibernate** for data persistence


---

## 🏗️ Architecture

<div align="center">

### *Microservices Ecosystem*

![System Architecture](screenshot/architecture.png)

</div>


## 🎥 Demo Video

<div align="center">

[![Watch Demo](https://img.shields.io/badge/▶️_Watch-Demo_Video-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://drive.google.com/file/d/1W6DbBleVEirqD2dcGncnXuZgucjKhuNK/view?usp=sharing)


</div>

### 🔄 Communication Patterns

| Pattern | Technology | Use Case |
|---------|-----------|----------|
| 🌐 **Synchronous** | REST APIs | Client ↔ Gateway communication |
| ⚡ **RPC** | gRPC + Protobuf | Patient ↔ Billing service |
| 📨 **Async Messaging** | Apache Kafka | Real-time analytics events |
| 🔐 **Authentication** | JWT Tokens | Secure service access |

---

## 🧩 Microservices Breakdown

<details open>
<summary><b>🚪 API Gateway</b> - The Front Door</summary>

- **Port:** `4000`
- **Responsibility:** Unified entry point for all client requests
- **Key Features:**
  - Request routing & load balancing
  - Authentication middleware
  - Rate limiting & circuit breaking
- **Tech Stack:** Spring Cloud Gateway

</details>

<details open>
<summary><b>🔐 Auth Service</b> - Security Guardian</summary>

- **Responsibility:** Authentication & Authorization
- **Key Features:**
  - JWT token generation & validation
  - User credential management
  - Role-based access control (RBAC)
- **Tech Stack:** Spring Security, JWT, JPA

</details>

<details open>
<summary><b>👨‍⚕️ Patient Service</b> - Core Domain Service</summary>

- **Port:** `4000` (via Gateway)
- **Responsibility:** Patient data management
- **Key Features:**
  - Full CRUD operations
  - gRPC client for billing integration
  - Kafka producer for analytics events
  - RESTful API endpoints
- **Tech Stack:** Spring Boot, JPA, gRPC Client, Kafka Producer

</details>

<details open>
<summary><b>💳 Billing Service</b> - Financial Operations</summary>

- **Responsibility:** Billing & payment processing
- **Key Features:**
  - High-performance gRPC server
  - Invoice generation & management
  - Payment transaction processing
  - Protocol Buffer contracts
- **Tech Stack:** Spring Boot, gRPC Server, Protobuf

**gRPC Contract:**
```protobuf
service BillingService {
  rpc CreateBill(BillRequest) returns (BillResponse);
  rpc GetBill(BillIdRequest) returns (BillResponse);
}
```

</details>

<details open>
<summary><b>📊 Analytics Service</b> - Insights Engine</summary>

- **Port:** `4000` (direct access)
- **Responsibility:** Real-time analytics & reporting
- **Key Features:**
  - Kafka consumer for event processing
  - Data aggregation & analytics
  - Dashboard metrics API
  - Historical reporting
- **Tech Stack:** Spring Boot, Kafka Consumer, JPA

</details>

---

## 🛠️ Technology Stack

<div align="center">

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Language** | ![Java](https://img.shields.io/badge/Java-25-orange?logo=java) | Primary programming language |
| **Framework** | ![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.0+-brightgreen?logo=spring) | Application framework |
| **Data** | ![JPA](https://img.shields.io/badge/Spring%20Data%20JPA-Data%20Layer-green?logo=spring) | ORM & database access |
| **Gateway** | ![Gateway](https://img.shields.io/badge/Spring%20Cloud%20Gateway-Routing-blue?logo=spring) | API gateway & routing |
| **Messaging** | ![Kafka](https://img.shields.io/badge/Apache%20Kafka-Event%20Bus-black?logo=apache-kafka) | Event streaming platform |
| **RPC** | ![gRPC](https://img.shields.io/badge/gRPC-Protobuf-blue?logo=grpc) | Inter-service communication |
| **Container** | ![Docker](https://img.shields.io/badge/Docker-Containerization-2496ED?logo=docker) | Application containerization |
| **Database** | ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-336791?logo=postgresql) | Relational database |

</div>

---

## 🔄 System Flows

### 🎯 Patient Registration Flow

```
┌─────────┐      ┌─────────┐      ┌─────────────┐      ┌──────────┐      ┌──────────┐
│ Client  │─────▶│   API   │─────▶│   Patient   │─────▶│  Billing │      │ Kafka    │
│         │      │ Gateway │      │   Service   │      │  Service │      │  Topic   │
└─────────┘      └─────────┘      └─────────────┘      └──────────┘      └──────────┘
                                          │                  ▲                   │
                                          │    gRPC Call     │                   │
                                          └──────────────────┘                   │
                                          │                                      │
                                          │         Kafka Event                  │
                                          └──────────────────────────────────────┘
                                                               │
                                                               ▼
                                                      ┌──────────────┐
                                                      │  Analytics   │
                                                      │   Service    │
                                                      └──────────────┘
```

### ⚡ Key Interaction Patterns

1. **Synchronous Request-Response** (REST)
   - Client → API Gateway → Microservices
   
2. **Remote Procedure Call** (gRPC)
   - Patient Service → Billing Service (high-performance billing operations)

3. **Event-Driven** (Kafka)
   - Patient Service publishes events → Kafka → Analytics Service consumes

---

## 📁 Project Structure

```
patient-management-system/
├── 📁 api-gateway/
│   ├── src/main/java/
│   ├── src/main/resources/
│   └── pom.xml
├── 📁 auth-service/
│   ├── src/main/java/
│   ├── src/main/resources/
│   └── pom.xml
├── 📁 patient-service/
│   ├── src/main/java/
│   ├── src/main/resources/
│   └── pom.xml
├── 📁 billing-service/
│   ├── src/main/java/
│   ├── src/main/proto/          # Protocol Buffer definitions
│   ├── src/main/resources/
│   └── pom.xml
├── 📁 analytics-service/
│   ├── src/main/java/
│   ├── src/main/resources/
│   └── pom.xml
├── 🐳 docker-compose.yml
├── 📄 .env.example
├── 📋 pom.xml                    # Parent POM
└── 📖 README.md
```

---

## 🔐 Security

- 🔒 **JWT Authentication** - Stateless token-based auth
- 🛡️ **API Gateway Security** - Centralized security policies
- 🔑 **Service-to-Service Auth** - gRPC metadata authentication
- 🔐 **Environment Variables** - Sensitive data protection
- 🚫 **CORS Configuration** - Cross-origin request handling
- 📝 **Audit Logging** - Complete request tracing via Kafka

---
---

## 👨‍💻 Author

**[Himanshu Arya]**

- GitHub: [Himanshu Arya](https://github.com/hkarya625)

---

## 🙏 Acknowledgments

- [Spring Boot](https://spring.io/projects/spring-boot) - Amazing framework
- [Apache Kafka](https://kafka.apache.org) - Reliable event streaming
- [gRPC](https://grpc.io) - High-performance RPC framework
- [Docker](https://www.docker.com) - Containerization platform

