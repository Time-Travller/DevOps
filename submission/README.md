# Node.js Microservices - Docker Compose

## Project Overview

This project contains four Node.js microservices containerized using Docker and orchestrated using Docker Compose.

### Services

| Service | Port | Endpoint |
|---|---:|---|
| User Service | 3000 | `/users` |
| Product Service | 3001 | `/products` |
| Order Service | 3002 | `/orders` |
| Gateway Service | 3003 | `/health` |

The Gateway Service communicates with the User, Product, and Order services using a shared Docker network.

---

## Project Structure

```text
submission/
├── user-service/
│   └── Dockerfile
├── product-service/
│   └── Dockerfile
├── order-service/
│   └── Dockerfile
├── gateway-service/
│   └── Dockerfile
├── docker-compose.yml
└── README.md

Prerequisites
Docker
Docker Compose

Check Docker:

docker --version

Check Docker Compose:

docker-compose --version
Setup

Build the Docker images:

docker-compose build

Start all services:

docker-compose up -d

Check running containers:

docker-compose ps

Stop all services:

docker-compose down
Port Mapping
localhost:3000 → User Service
localhost:3001 → Product Service
localhost:3002 → Order Service
localhost:3003 → Gateway Service
Testing
User Service
curl http://localhost:3000/users
Product Service
curl http://localhost:3001/products
Order Service
curl http://localhost:3002/orders

The initial response may be:

[]
Gateway Health
curl http://localhost:3003/health
Gateway → User
curl http://localhost:3003/api/users
Gateway → Product
curl http://localhost:3003/api/products
Gateway → Order
curl http://localhost:3003/api/orders
Docker Network

All four services are connected to the shared Docker network:

microservices-network

The Gateway communicates with the other services using their Docker service names:

http://user-service:3000
http://product-service:3001
http://order-service:3002
Troubleshooting

Check container status:

docker-compose ps

Check logs:

docker-compose logs

Check logs for a specific service:

docker-compose logs gateway-service

Check Docker networks:

docker network ls

Rebuild after making changes:

docker-compose down
docker-compose build
docker-compose up -d
Validation

All four services were successfully containerized and started using Docker Compose.

The following communication was successfully tested:

Gateway → User Service
Gateway → Product Service
Gateway → Order Service
Screenshots
Docker Containers Running


docker-compose ps


Gateway API Testing


curl http://localhost:3003/api/users
curl http://localhost:3003/api/products
curl http://localhost:3003/api/orders
