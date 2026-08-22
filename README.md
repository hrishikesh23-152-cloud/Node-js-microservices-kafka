# Microservices Backend Platform

A backend system built with **Node.js, TypeScript, PostgreSQL, Apache Kafka, Redis, and Docker**, following a microservices-oriented architecture.

The project explores how independent backend services communicate, process asynchronous events, share infrastructure, and scale independently.

> 🚧 **Project Status:** In Development

## 🏗️ Architecture

The system is organized around multiple independent services that communicate through APIs and **Apache Kafka** for asynchronous, event-driven communication.

```text
                    ┌─────────────────┐
                    │    API Gateway  │
                    └────────┬────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
              ▼              ▼              ▼
        ┌───────────┐  ┌───────────┐  ┌───────────┐
        │ Service A │  │ Service B │  │ Service C │
        └─────┬─────┘  └─────┬─────┘  └─────┬─────┘
              │              │              │
              └──────────────┼──────────────┘
                             ▼
                    ┌─────────────────┐
                    │  Apache Kafka   │
                    │ Topics / Events │
                    └─────────────────┘
                             │
                    ┌────────┴────────┐
                    ▼                 ▼
              ┌───────────┐    ┌───────────┐
              │ PostgreSQL│    │   Redis   │
              └───────────┘    └───────────┘
```

## 🛠️ Tech Stack

* **Node.js** — Backend runtime
* **TypeScript** — Type-safe backend development
* **PostgreSQL** — Relational database
* **Apache Kafka** — Event streaming and asynchronous service communication
* **Redis** — Caching and fast data access
* **Docker** — Containerization and local infrastructure
* **Git & GitHub** — Version control

## 🔄 Kafka-Based Communication

Apache Kafka is used to enable **asynchronous communication between microservices**.

Instead of tightly coupling services through synchronous HTTP requests, services can publish events to Kafka topics and other services can consume those events independently.

Example:

```text
Order Service
      │
      │ publish event
      ▼
  Kafka Topic
      │
      ├──────────────► Payment Service
      │
      └──────────────► Notification Service
```

This architecture helps improve:

* Service decoupling
* Asynchronous processing
* Scalability
* Fault tolerance
* Event-driven architecture

## ⚡ Redis

Redis is used for high-speed in-memory operations such as caching and reducing unnecessary database queries.

```text
Client
  │
  ▼
Service
  │
  ├──► Redis ──► Cache Hit
  │
  └──► PostgreSQL ──► Cache Miss
```

## 🐳 Docker

Docker is used to containerize the application and supporting infrastructure.

The Docker configuration is maintained inside:

```text
docker/
```

This allows the development environment and infrastructure dependencies to be reproduced consistently.

## 🗄️ Database

SQL schemas and database-related scripts are maintained inside:

```text
sql/
```

PostgreSQL is used for persistent relational data storage.

## 📦 Shared Packages

Reusable functionality shared between services is maintained inside:

```text
packages/
```

This helps reduce code duplication and provides common utilities across the microservices.

## 📁 Project Structure

```text
nodejs-microservices/
│
├── app/                 # Microservices and application code
├── docker/              # Docker configuration
├── packages/            # Shared packages
├── scripts/             # Development/automation scripts
├── sql/                 # SQL schemas and migrations
│
├── .gitignore
├── package.json
├── package-lock.json
└── tsconfig.base.json
```

## 🚀 Getting Started

### Clone the repository

```bash
git clone <your-repository-url>
cd nodejs-microservices
```

### Install dependencies

```bash
npm install
```

### Configure environment variables

Create a `.env` file containing the required configuration.

**Never commit `.env` or credentials to GitHub.**

### Start infrastructure

```bash
docker compose up
```

The exact command may vary depending on the current Docker configuration.

## 🎯 Learning Objectives

This project is being developed to gain practical experience with:

* Microservices architecture
* Event-driven architecture
* Apache Kafka
* Kafka producers and consumers
* Service-to-service communication
* Redis caching
* PostgreSQL
* Docker and containerization
* Distributed-system concepts
* Scalability
* Fault tolerance
* Database design
* Backend architecture

## 🔮 Future Improvements

Planned improvements include:

* [ ] Complete and refine individual microservices
* [ ] Expand Kafka event-driven workflows
* [ ] Improve Redis caching strategies
* [ ] Add comprehensive API validation
* [ ] Improve authentication and authorization
* [ ] Add structured logging
* [ ] Add automated testing
* [ ] Improve monitoring and observability
* [ ] Improve fault handling and retry mechanisms
* [ ] Document complete system architecture

## 📌 Project Status

**In Development**

The project is actively being developed and expanded to explore production-oriented backend and distributed-system concepts.

## 👨‍💻 Author

**Hrishikesh Bharadwaj**

Computer Science Engineering Student
