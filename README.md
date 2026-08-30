# LMS Cloud Project Platform

This repository contains the **cloud platform and infrastructure services** for the Learning Management System (LMS) microservices architecture.

The platform provides centralized configuration, service discovery, and API routing for the LMS backend services.

## 📦 Platform Services

### 1. API Gateway

The **API Gateway** acts as the main entry point for client applications.

Responsibilities:

- Route client requests to backend microservices
- Provide a single entry point for the system
- Integrate with service discovery
- Handle cross-origin requests
- Support load-balanced service routing

### 2. Config Server

The **Config Server** provides centralized configuration management for the LMS microservices.

Responsibilities:

- Manage application configuration centrally
- Provide configuration to microservices
- Reduce duplicated configuration
- Support environment-based configuration

### 3. Service Registry

The **Service Registry** uses Netflix Eureka for service discovery.

Responsibilities:

- Register microservices
- Discover available service instances
- Enable communication between microservices
- Support dynamic service discovery

<img width="1672" height="951" alt="image" src="https://github.com/user-attachments/assets/f79e34fe-9e90-4cf0-aa45-5137c5a06bb7" />

## 🏗️ Architecture

```text
                          ┌──────────────────┐
                          │     Frontend     │
                          └────────┬─────────┘
                                   │
                                   ▼
                          ┌──────────────────┐
                          │   API Gateway    │
                          └────────┬─────────┘
                                   │
                 ┌─────────────────┼─────────────────┐
                 │                 │                 │
                 ▼                 ▼                 ▼
         ┌──────────────┐  ┌──────────────┐  ┌────────────────┐
         │ User Service │  │ Book Service │  │ Borrowing      │
         │              │  │              │  │ Service        │
         └──────────────┘  └──────────────┘  └────────────────┘

                  ▲
                  │ Service Discovery
                  │
         ┌────────────────────┐
         │  Service Registry  │
         │      Eureka        │
         └────────────────────┘

                  ▲
                  │ Configuration
                  │
         ┌────────────────────┐
         │   Config Server    │
         └────────────────────┘


         
