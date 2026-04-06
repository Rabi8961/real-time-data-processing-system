# Real-Time Data Processing System

## 🚀 Overview
This project simulates a real-time data ingestion system designed to handle large-scale device data using gRPC and asynchronous processing.

---

## 🏗️ Architecture

```mermaid
flowchart LR

%% Clients / Devices
A[Device Simulator / IoT Devices] -->|gRPC Streaming| B[Ingestion Service (Node.js gRPC)]

%% Ingestion Layer
B -->|Publish Events| C[Message Queue (Pub/Sub / Kafka)]

%% Processing Layer
C --> D1[Worker Service 1]
C --> D2[Worker Service 2]
C --> D3[Worker Service N]

%% Data Storage
D1 -->|Processed Data| E[BigQuery / PostgreSQL]
D2 -->|Processed Data| E
D3 -->|Processed Data| E

%% Cold Storage
E -->|Archive Old Data| F[Cloud Storage]

%% API Layer
E --> G[Analytics API Service]

%% Dashboard
G --> H[Dashboard / Client UI]

%% Security & Config
I[Secret Manager] --> B
I --> D1
I --> D2
I --> D3

J[Service Accounts / IAM] --> B
J --> D1
J --> D2
J --> D3

%% Deployment
K[GKE Cluster] --> B
K --> D1
K --> D2
K --> D3

L[Cloud Run] --> G
```

---

## ⚙️ Tech Stack
- Node.js (gRPC)
- Redis / Kafka
- PostgreSQL
- Docker

---

## 🔄 Data Flow

Devices → gRPC Server → Queue → Workers → Database

---

## ⚡ Key Features

- gRPC streaming ingestion
- Event-driven architecture
- Horizontal scaling with workers
- Fault-tolerant processing

---

## 📈 Scaling Strategy

- Stateless ingestion service
- Parallel worker processing
- Queue-based decoupling

---

## 💰 Cost Optimization (Inspired by production)

- Data retention strategy
- Batch processing
- Efficient storage usage

---

## 🧠 Learnings

- Async processing improves scalability
- Worker-based architecture increases throughput
- Trade-offs between consistency and performance
