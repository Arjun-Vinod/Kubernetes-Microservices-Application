
# Kubernetes Microservices Application

This project is a Kubernetes-based microservices application that demonstrates deploying a  Voting System on a Kubernetes cluster. The architecture is based on the popular example voting app, broken into multiple services, each running in its own container, and managed with Kubernetes deployments and services.



## Architecture

The application consists of 5 main components:

1.Voting App (Python – Frontend)
- A simple Python web app where users can cast votes (e.g., Cats vs Dogs).

- Votes are captured and stored in Redis (in-memory DB).

2.Redis (In-Memory Database)

- Stores incoming votes temporarily.

- Fast, lightweight, and used for real-time updates.

3.Worker (DotNet Service)

- Background processor that reads votes from Redis.

- Writes the processed votes permanently into Postgres DB.

4.Postgres (Database)

- Stores the votes in a persistent relational database.

- Secured with Kubernetes Secrets for username, password, and DB name.

5.Result App (Node.js – Frontend)

- Displays the voting results to users.

- Fetches data from Postgres through the backend.
## Kubernetes Objects

## Deployments
- `python-deployment.yaml`: Deploys the voting app.
- `node-deployment.yaml`: Deploys the result app.
- `worker-deployment.yaml`: Deploys the worker service.
- `postgres-deployment.yaml`: Deploys Postgres database with secrets.
- `redis-deployment.yaml`: Deploys Redis in-memory database.

## Services
- `python-service.yaml`: Exposes the voting app on port 30005 (LoadBalancer).
- `node-service.yaml`: Exposes the result app on port 30006 (LoadBalancer).
- `postgres-service.yaml`: Internal ClusterIP service for Postgres DB.
- `redis-service.yaml`: Internal ClusterIP service for Redis DB.

## Secrets
- `postgres-secret.yaml`: Stores database credentials (username, password, database name).
## How To Run

1.Apply Secrets

```bash
kubectl apply -f deployments/postgres-secret.yaml

```

3. Apply Deployments

```bash
kubectl apply -f deployments/

```
4. Apply Services

```bash
kubectl apply -f services/

```
5. Verify Pods and Services

```bash
kubectl get pods
kubectl get svc

```



## Features

- Microservices-based architecture.

- Uses Kubernetes Deployments, Services, and Secrets.

- Demonstrates LoadBalancer service exposure.
