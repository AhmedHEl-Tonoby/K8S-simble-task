# Voting App Microservices Project

This project is a microservices-based **Voting Application** that consists of five different deployments, including the main voting application, Redis, PostgreSQL, a worker, and a result page. The application is designed to allow users to vote and view real-time results, with a backend that manages state using Redis and PostgreSQL.

## Project Structure

The project is composed of the following services:

1. **Voting App** - The main application where users can submit their votes.
2. **Redis** - An in-memory data structure store used to manage vote queues.
3. **PostgreSQL** - A relational database used for persisting the results.
4. **Worker pod** - Processes the votes from Redis and stores them in PostgreSQL.
5. **Result Page** - Displays the results of the voting in real-time.

### Kubernetes Setup

- Each component has been deployed as a separate **Kubernetes Deployment** to ensure isolation and scalability.
- **Services** have been created to enable communication between these components, and to expose specific applications externally.

### Services Configuration

- **PostgreSQL and Redis** are configured as **ClusterIP** services. This ensures they are only accessible within the cluster for secure and internal communication between the pods.
- **Voting App** and **Result Page** are configured as **NodePort** services, allowing them to be accessed externally from outside the Kubernetes cluster.

### Kubernetes Objects

Here’s a breakdown of the objects used in the project:

1. **Deployments**:
   - 5 deployments in total, each for the Voting App, Redis, PostgreSQL, Worker Instance, and Result Page.
   - These deployments ensure that each service runs as a set of replicas in the cluster, providing scalability and high availability.

2. **Services**:
   - **ClusterIP** services for Redis and PostgreSQL, which allows the backend components to communicate internally within the cluster.
   - **NodePort** services for the Voting App and Result Page, enabling access to the frontend interfaces from outside the cluster.

### How to Access the App

- The **Voting App** can be accessed through a browser using the **NodePort** URL provided by Kubernetes.
- The **Result Page** is also accessible via a **NodePort** URL, where you can monitor live voting results.

### Technology Stack

- **Backend**: PostgreSQL, Redis
- **Frontend**: Voting App and Result Page (Accessible via NodePort)
- **Worker Instance**: Processes data and stores results in PostgreSQL
- **Orchestration**: Kubernetes

## Prerequisites

To deploy and run this project, you will need:

- Kubernetes Cluster (Minikube, GKE, etc.)
- kubectl
- Docker


