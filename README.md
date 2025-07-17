## AWS-EKS-Deployment
# Kubernetes App Deployment on AWS EKS with EFS Persistent Storage

This project documents the setup and deployment of a containerized application on AWS Elastic Kubernetes Service (EKS) with an Amazon EFS (Elastic File System) volume integration to ensure persistent data storage and high availability, even during downtime or pod restarts.



This was a fully functional microservices-based application deployed using Kubernetes on AWS. The architecture touches every critical AWS and Kubernetes component to demonstrate a complete production-ready setup.

Key Components & Features

 ⚙️ Amazon EKS Cluster
- Created via eksctl and AWS CloudFormation templates.
- Includes a managed Node Group, provisioning EC2 instances automatically. This was done behind the scene by the Kubernetes during the EKS Cluster setup
- Integrated with IAM roles for secure access.

 📦 Amazon EFS (Elastic File System)
- Set up StorageClass, PersistentVolume (PV), and PersistentVolumeClaim (PVC).
- EFS volumes were mounted directly into containers to retain application data even during node failures or pod evictions.
- Ensures data persistence and stateful workloads.

 🧾 Kubernetes Resources Used
- Deployments for application pods.
- Services:
  - `LoadBalancer` services for external-facing modules.
  - `ClusterIP` for internal-only modules like authentication. This was used specifically for the Auth-api side of the application as it communication is basically internal and not expected to to be reached externally.
- Namespaces for logical separation and service communication.
- ConfigMaps & Secrets for dynamic environment configuration and secure credentials.

 🌐 Networking
- Integrated with AWS Load Balancers to expose frontend and APIs.
- DNS resolution and internal communication managed seamlessly via Kubernetes service discovery.

 🔐 Security & IAM
- Roles were assigned to pods using IAM Roles for Service Accounts (IRSA).
- Fine-grained access configured to allow pods interact with EFS and other AWS services securely.


 💡 Highlights
- Persistent storage enabled using Amazon EFS — survives pod rescheduling and downtime.
- Modular architecture with microservices deployed in separate pods.
- Fully integrated with AWS best practices for security, networking, and scaling.
- Handled CORS origin issues in code to allow seamless API communication.
- Production-grade setup that can scale and evolve easily with CI/CD pipelines.




