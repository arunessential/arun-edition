# Arun's Edition – Luxury Marketplace on AWS

## Overview

**Arun's Edition** is a luxury marketplace website inspired by platforms like JamesEdition.
It showcases premium products such as luxury cars, yachts, and high-end properties.

The application is deployed on **AWS using a secure and highly available architecture** that follows DevOps and cloud best practices. The infrastructure is designed to support **high availability, scalability, cost optimization, and zero downtime deployments**.

---

# Website Structure

The website uses **path-based routing** to organize content.

### Main Landing Page

```
/home
```

### Sections inside Home

```
/cars
/yachts
/properties
```

Example URLs:

```
http://<load-balancer-dns>/home
http://<load-balancer-dns>/cars
http://<load-balancer-dns>/yachts
http://<load-balancer-dns>/properties
```

---

# Repository Structure

```
aruns-edition
│
├── home
│   └── index.html
│
├── cars
│   └── index.html
│
├── yachts
│   └── index.html
│
├── properties
│   └── index.html
│
├── assets
│   ├── css
│   └── images
│
└── README.md
```

This structure ensures a **clean CI/CD workflow** and allows the load balancer to route traffic correctly.

---

# AWS Infrastructure Architecture

The application is deployed inside a custom **AWS VPC architecture**.

### Network Design

```
VPC
│
├── Public Subnet 1
├── Public Subnet 2
│
├── Private Subnet 1
├── Private Subnet 2
└── Private Subnet 3
```

### Key Components

**Internet Gateway**

* Enables internet access to public resources.

**NAT Gateway**

* Allows private instances to access the internet securely for updates and package installations.

**Bastion Host**

* Located in the public subnet.
* Used for secure SSH access to private EC2 instances.

**Route Tables**

* Control network traffic between subnets, NAT gateway, and internet gateway.

---

# Load Balancing

The application uses an **Application Load Balancer (ALB)**.

Functions:

* Distributes incoming traffic across instances.
* Provides **high availability**.
* Implements **path-based routing**.

### Path Based Routing Example

```
/home        → Home page
/cars        → Cars section
/yachts      → Yachts section
/properties  → Properties section
```

---

# Auto Scaling

An **Auto Scaling Group (ASG)** is configured to automatically scale EC2 instances based on system load.

Benefits:

* Automatic scaling during traffic spikes
* Reduced infrastructure cost during low traffic
* High availability across multiple availability zones

---

# Security Architecture

Security best practices implemented:

* EC2 instances hosted in **private subnets**
* Direct public access to application servers **disabled**
* SSH access only via **Bastion Host**
* Security Groups restrict inbound traffic
* Load balancer acts as the **only public entry point**

---

# Kubernetes Deployment (Planned)

The project will be extended to deploy the application using **Kubernetes for improved scalability and orchestration**.

Key goals:

* Containerized deployment
* Zero downtime updates
* Efficient scaling
* Cost optimization

Possible implementation:

* Amazon EKS cluster
* Kubernetes Deployments
* Kubernetes Services
* Horizontal Pod Autoscaler

---

# High Availability

The infrastructure is designed for high availability by using:

* Multiple public subnets
* Multiple private subnets
* Load balancing
* Auto scaling
* Multi-AZ deployment

This ensures the application remains available even if one availability zone fails.

---

# Cost Optimization Strategy

To minimize operational costs:

* Auto Scaling adjusts resources dynamically
* Kubernetes cluster will utilize efficient resource scheduling
* Potential use of **Spot Instances for worker nodes**
* Right-sized instance types

---

# Monitoring and Observability (Planned)

The system will integrate monitoring tools such as:

* Prometheus
* Grafana

Metrics to monitor:

* CPU usage
* Memory usage
* Application health
* Server performance
* Traffic patterns

---

# DevOps Workflow

Typical workflow:

```
Developer
   ↓
GitHub Repository
   ↓
CI/CD Pipeline
   ↓
Build & Test
   ↓
Deployment to AWS Infrastructure
```

Future improvements include:

* Automated CI/CD pipelines
* Container image builds
* Kubernetes deployments

---

# Project Goals

* Build a scalable cloud-native web platform
* Implement secure AWS networking architecture
* Demonstrate DevOps best practices
* Enable highly available and cost-efficient deployments

---

# Author

**Arun Rout**

DevOps | Cloud | Infrastructure Engineering
