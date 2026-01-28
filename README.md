# Audi Cloud Migration: Monolith to Cloud-Native Microservices

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?logo=amazon-aws) 
![Kubernetes](https://img.shields.io/badge/Orchestration-EKS-blue?logo=kubernetes) 
![Terraform](https://img.shields.io/badge/IaC-Terraform-purple?logo=terraform) 
![Karpenter](https://img.shields.io/badge/Scaling-Karpenter-green)

## 📖 Executive Summary
This project details the architectural transformation of Audi's car configurator platform—a highly business-critical application used by dealers and customers worldwide. 

To address challenges with on-premises scalability, resource overprovisioning, and global latency, the system was migrated from a monolithic architecture to a containerized microservices architecture on **Amazon EKS**. A key component of this solution is the implementation of **Karpenter**, allowing for rapid, cost-effective, and flexible node autoscaling[cite: 39].

## 🏗️ Architecture Blueprint
*(See `assets/diagrams` for the full schematic)*

![Architecture Diagram](assets/diagrams/audi-architecture.png)

### Key Architectural Decisions

| Challenge | Solution Implemented | Rationale |
| :--- | :--- | :--- |
| **Monolithic Scalability** | **Amazon EKS (Microservices)** | [Split the monolith into containers to allow independent scaling and updates for individual markets. |
| **Slow Provisioning** | **Terraform & CloudFormation** | Adopted a hybrid Infrastructure as Code (IaC) approach to speed up environment setup from weeks to minutes. |
| **Cost & Agility** | **Karpenter** | Replaced standard autoscalers with Karpenter to dynamically provision rightsized EC2 instances (Spot/On-Demand) and support multi-architecture nodes. |
| **Global Latency** | **AWS Regions** | Deployed workloads in regions physically closer to overseas customers to reduce latency. |
| **Stability** | **Blue/Green Deployments** | Implemented traffic-shifting strategies to cover resource spikes and ensure safe releases. |

## 📂 Repository Structure

* `docs/`: Detailed implementation guide explaining the migration logic.
* `infrastructure/`: Terraform modules for VPC, EKS, and Karpenter setup.
* `assets/`: Architectural diagrams and reference images.

## 🛠️ Getting Started

To initialize the infrastructure plan:

```bash
cd infrastructure
terraform init
terraform plan
