# Audi Cloud Migration: Monolith to Cloud-Native Microservices on AWS

![AWS](https://img.shields.io/badge/AWS-Cloud-orange) ![Terraform](https://img.shields.io/badge/Infrastructure-Terraform-purple) ![Kubernetes](https://img.shields.io/badge/Orchestration-EKS-blue)

## 📖 Executive Summary
[cite_start]This project outlines the architectural transformation of Audi's car configurator platform from an on-premises monolithic application to a scalable, global microservices architecture on Amazon AWS[cite: 16, 20].

[cite_start]The solution leverages **Amazon EKS** for orchestration and **Karpenter** for just-in-time node provisioning, addressing critical issues regarding latency, resource overprovisioning, and deployment agility[cite: 25, 39].

## 🏗️ Architecture Blueprint
*(Place your Draw.io diagram in assets/diagrams and it will appear here)*
![Architecture Diagram](assets/diagrams/audi-architecture-v1.png)

### Key Architectural Decisions
| Component | Technology | Rationale |
| :--- | :--- | :--- |
| **Compute** | Amazon EKS | [cite_start]Migrated to containerized architecture to split monolith into microservices[cite: 37]. |
| **Autoscaling** | **Karpenter** | [cite_start]Replaces standard autoscaler to optimize EC2 purchasing options and handle spikes instantly[cite: 39]. |
| **IaC** | Terraform & CloudFormation | [cite_start]Hybrid approach to infrastructure automation as utilized by Audi's team[cite: 32]. |
| **Latency** | AWS Regions | [cite_start]Deployed workloads closer to overseas customers to solve latency issues[cite: 29]. |

## 🚀 Implementation Strategy
1.  **Network Layer:** Multi-AZ VPC deployment for high availability.
2.  [cite_start]**Compute Layer:** EKS Cluster utilizing **Cluster Autoscaler** and **Karpenter** for efficient resource management[cite: 37, 39].
3.  [cite_start]**Deployment:** Blue/Green deployment strategy to stabilize the environment during updates[cite: 34].

## 📂 Repository Structure
* `/docs`: Detailed implementation guide and case study analysis.
* `/infrastructure`: Terraform configuration files broken down by modules.

## 🛠️ Getting Started
To view the infrastructure plan:
```bash
cd infrastructure/terraform
terraform init
terraform plan
