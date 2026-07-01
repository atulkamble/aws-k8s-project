# 🚀 AWS EKS Deployment Project (Python + Docker + ECR + Kubernetes)

## 📌 Project Workflow

```text
Plan (Architect)
        │
        ▼
Development (Developer)
        │
        ▼
Local Testing
        │
        ▼
Docker Containerization
        │
        ▼
Amazon ECR
        │
        ▼
Amazon EKS (Kubernetes)
        │
        ▼
Production Deployment
```

---

# 🛠️ Required Tools

| Tool           | Purpose                        |
| -------------- | ------------------------------ |
| Python         | Application Development        |
| AWS CLI        | Manage AWS Resources           |
| eksctl         | Create and Manage EKS Clusters |
| kubectl        | Kubernetes Command Line Tool   |
| Docker Desktop | Build and Run Containers       |
| Git            | Version Control                |
| GitHub Account | Source Code Repository         |

---

# ☁️ AWS Services Used

| Service                          | Description                                             |
| -------------------------------- | ------------------------------------------------------- |
| AWS CloudFormation               | Infrastructure as Code (IaC) using Stacks               |
| IAM                              | Identity and Access Management                          |
| EC2                              | Elastic Compute Cloud (Virtual Machines / Worker Nodes) |
| EKS                              | Elastic Kubernetes Service (Kubernetes Cluster)         |
| Auto Scaling Group (ASG)         | Automatically Scales Worker Nodes                       |
| Elastic Load Balancer (ELB)      | Distributes Incoming Traffic                            |
| Elastic Container Registry (ECR) | Docker Image Registry                                   |
| VPC                              | Virtual Private Cloud                                   |
| Subnet                           | Network Segmentation                                    |
| Elastic IP                       | Static Public IP Address                                |

---

# 👤 IAM Setup

```
IAM
 └── User (atul)
      └── Group (Admin)

Permissions:
✔ AdministratorAccess

Create:
• Access Key
• Secret Access Key
```

---

# 👨‍💻 Team Roles

### Kubernetes Administrator

* Create and manage EKS Cluster
* Cluster Maintenance
* Security

### Developer

* Develop Application
* Push Code to Git Repository

### Cloud Administrator

* Build Docker Image
* Deploy Application
* Manage Infrastructure

### Tester

* Test Application
* Validate Deployment

---

# 🏗️ Application Architecture

```text
User
   │
   ▼
Load Balancer
   │
   ▼
Kubernetes Nodes
   │
   ▼
Pods
   │
   ▼
Python Application
   │
   ▼
Web UI
```

---

# 📁 Project Repository

```bash
cd Downloads

git clone https://github.com/atulkamble/aws-k8s-project.git

cd aws-k8s-project

code .
```

Project Structure

```text
.
├── app.py
├── requirements.txt
└── templates
    └── index.html
```

---

# 🐍 Local Development

Check versions

```bash
python --version
pip --version
```

Install dependencies

```bash
pip install -r requirements.txt
```

Run application

```bash
python app.py
```

Open

```
http://localhost:5000/
```

---

# 📝 Git Version Control

```bash
git add .

git commit -m "dev"

git push origin main
```

✅ Development Phase Completed

---

# 🐳 Docker Phase

Build Docker Image

```bash
docker build -t app .
```

View Images

```bash
docker images
```

Run Container

```bash
docker run -d -p 5000:5000 app:latest
```

View Running Containers

```bash
docker container ls
```

Open

```
http://localhost:5000/
```

---

# 📦 Amazon ECR Phase

Create Repository

```
cloudnautic/pythonapp
```

Login

```bash
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 535002879962.dkr.ecr.us-east-1.amazonaws.com
```

Build Image

```bash
docker build --platform linux/amd64,linux/arm64 -t cloudnautic/pythonapp .
```

Tag Image

```bash
docker tag cloudnautic/pythonapp:latest 535002879962.dkr.ecr.us-east-1.amazonaws.com/cloudnautic/pythonapp:latest
```

Push Image

```bash
docker push 535002879962.dkr.ecr.us-east-1.amazonaws.com/cloudnautic/pythonapp:latest
```

Pull Image

```bash
docker pull 535002879962.dkr.ecr.us-east-1.amazonaws.com/cloudnautic/pythonapp:latest
```

Run Container

```bash
docker run -d -p 5000:5000 535002879962.dkr.ecr.us-east-1.amazonaws.com/cloudnautic/pythonapp:latest
```

Verify

```bash
docker images

docker container ls
```

Open

```
http://localhost:5000/
```

---

# ☸️ Amazon EKS

## Kubernetes Hierarchy

```text
Application
      │
      ▼
Container
      │
      ▼
Pod
      │
      ▼
Node
      │
      ▼
Cluster
```

---

## Create EKS Cluster

```bash
eksctl create cluster \
--name mycluster \
--region us-east-1 \
--nodegroup-name mynodes \
--node-type t3.medium \
--nodes 3 \
--nodes-min 2 \
--nodes-max 4 \
--managed
```

---

## Configure kubectl

```bash
aws eks update-kubeconfig \
--name mycluster \
--region us-east-1
```

---

# ☸️ Kubernetes Deployment

Deploy Application

```bash
kubectl apply -f deployment.yaml

kubectl apply -f service.yaml
```

Check Nodes

```bash
kubectl get nodes
```

Check Pods

```bash
kubectl get pods
```

Check Services

```bash
kubectl get services
```

---

# 🌐 Access Application

Load Balancer URL

```text
acce625b28d3941508d3da833297d2f4-862346573.us-east-1.elb.amazonaws.com
```

Open in Browser

```text
http://acce625b28d3941508d3da833297d2f4-862346573.us-east-1.elb.amazonaws.com
```

---

# 📚 End-to-End Deployment Flow

```text
Plan
   │
   ▼
Create AWS Infrastructure
   │
   ▼
Configure AWS CLI
   │
   ▼
Develop Python Application
   │
   ▼
Git Commit
   │
   ▼
Push to GitHub
   │
   ▼
Build Docker Image
   │
   ▼
Push Image to Amazon ECR
   │
   ▼
Create Amazon EKS Cluster
   │
   ▼
Deploy Kubernetes Resources
   │
   ▼
Create Load Balancer
   │
   ▼
Access Application in Browser
```
### delete cluster 
```
eksctl delete cluster --name mycluster --region us-east-1
```
