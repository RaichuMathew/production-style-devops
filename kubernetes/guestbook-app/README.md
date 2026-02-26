# Kubernetes Guestbook Application

## Architecture

Three-tier architecture:

1. Redis Master (1 replica)
2. Redis Slave (2 replicas)
3. Frontend (3 replicas)

---

## Backend Tier

### Redis Master
- Image: redis:latest
- Resources: 100Mi / 100m
- Port: 6379

### Redis Slave
- Image: gcr.io/google_samples/gb-redisslave:v3
- Environment variable: GET_HOSTS_FROM=dns
- Resources: 100Mi / 100m
- Port: 6379

---

## Frontend Tier

- Image: gcr.io/google-samples/gb-frontend:v4
- Replicas: 3
- NodePort: 30009
- Port: 80
- GET_HOSTS_FROM=dns

---

## Concepts Demonstrated

- Multi-tier architecture
- Service discovery via DNS
- Resource requests
- Scaling replicas
- NodePort service exposure

---

## Deploy

kubectl apply -f guestbook.yaml
