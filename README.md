# 🚀 Featured Projects

<div align="center">

### Engineering projects focused on Cloud, DevOps, Automation, Kubernetes, FinOps & IoT

<br/>

![AWS](https://img.shields.io/badge/AWS-Cloud-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Cloud_Native-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-IaC-844FBA?style=flat-square&logo=terraform&logoColor=white)
![Python](https://img.shields.io/badge/Python-Automation-3776AB?style=flat-square&logo=python&logoColor=white)
![DevOps](https://img.shields.io/badge/DevOps-Automation-success?style=flat-square)

</div>

---

## 📌 Project Portfolio

| Project | Domain | Core Technologies |
|---|---|---|
| 💰 **AWS Multi-Region Cost Optimization Platform** | FinOps / Cloud Automation | Lambda, Python, Boto3, SES, EventBridge |
| 🤖 **OpsPilot** | Kubernetes / DevOps / SRE | EKS, Docker, Kubernetes, Prometheus, Grafana |
| 🔐 **DevSecOps Cloud Platform** | DevSecOps / GitOps | Terraform, EKS, ArgoCD, Helm, CI/CD |
| 🪙 **Gold & Silver Price Monitoring System** | Serverless / Automation | Lambda, DynamoDB, SES, Python |
| ❤️ **IoT Health Monitoring System** | IoT / Embedded | ESP32, MAX30102, MPU6050, Embedded C |

---

# ⭐ 01 — AWS Multi-Region Cost Optimization Platform

> **Serverless FinOps automation that discovers unused AWS resources across multiple regions and estimates potential monthly cloud savings.**

<div align="center">

![AWS Lambda](https://img.shields.io/badge/AWS_Lambda-FF9900?style=for-the-badge&logo=awslambda&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Amazon CloudWatch](https://img.shields.io/badge/CloudWatch-FF4F8B?style=for-the-badge&logo=amazoncloudwatch&logoColor=white)
![Amazon EventBridge](https://img.shields.io/badge/EventBridge-FF4F8B?style=for-the-badge&logo=amazoneventbridge&logoColor=white)

</div>

<details open>
<summary><b>💡 Click to explore the project</b></summary>

<br/>

### 🎯 Problem

Unused cloud resources can continue generating costs even when they are no longer providing business value.

Manually checking every AWS region for unused infrastructure is repetitive and error-prone.

### 💡 Solution

I built a **serverless AWS cost optimization monitoring system** that automatically scans configured AWS regions, identifies potentially unused resources, estimates monthly savings and sends a consolidated HTML report through email.

### 🏗️ Architecture

```mermaid
flowchart TD

    EB["⏰ Amazon EventBridge"] --> L["⚡ AWS Lambda"]

    L --> REG["🌍 Scan AWS Regions"]

    REG --> EC2["EC2"]
    REG --> EBS["EBS"]
    REG --> EIP["Elastic IP"]
    REG --> NAT["NAT Gateway"]
    REG --> LB["Load Balancer"]
    REG --> SNAP["Snapshots"]

    EC2 --> ANALYZE["🔎 Analyze Unused Resources"]
    EBS --> ANALYZE
    EIP --> ANALYZE
    NAT --> ANALYZE
    LB --> ANALYZE
    SNAP --> ANALYZE

    ANALYZE --> COST["💰 Estimate Savings"]

    COST --> HTML["📄 Generate HTML Report"]

    HTML --> SES["📧 Amazon SES"]

    SES --> USER["👨‍💻 Email Report"]
```

### 🔍 Resources Monitored

- Stopped EC2 instances
- Unattached EBS volumes
- Old EBS snapshots
- Unused Elastic IP addresses
- Potentially idle NAT Gateways
- Potentially idle Load Balancers

### ⚙️ Execution Flow

```text
EventBridge
      │
      ▼
AWS Lambda
      │
      ▼
Discover Enabled Regions
      │
      ▼
Scan Resources
      │
      ▼
Detect Unused Infrastructure
      │
      ▼
Estimate Monthly Savings
      │
      ▼
Generate HTML Report
      │
      ▼
Amazon SES
      │
      ▼
Email Notification
```

### 🧠 Automation Logic

Example regional client creation:

```python
for region in regions:
    ec2 = boto3.client("ec2", region_name=region)
```

Example EBS cost estimation:

```text
Unused EBS Volume

Size = 100 GB
Estimated rate = $0.08 / GB

Estimated saving:

100 × $0.08
= $8 / month
```

### 📧 Generated Report

The automated report contains information such as:

| Region | Resource | Finding | Estimated Saving | Recommendation |
|---|---|---|---:|---|
| us-east-1 | EBS | Unattached volume | Estimated | Review / Delete |
| ap-south-1 | EC2 | Stopped instance | Estimated | Review |
| eu-west-1 | EIP | Unassociated IP | Estimated | Release |

### 🧰 Technologies

`AWS Lambda`
`EventBridge`
`CloudWatch`
`Amazon SES`
`AWS IAM`
`Python`
`Boto3`

### 🎯 Skills Demonstrated

- AWS Serverless Architecture
- Python Automation
- Boto3
- Multi-region AWS operations
- Cloud Cost Optimization
- FinOps fundamentals
- IAM permissions
- Event-driven architecture
- HTML report generation
- Automated cloud auditing

</details>

---

# 🤖 02 — OpsPilot

## Kubernetes Self-Healing & AI-Assisted Microservices Platform

> **A Kubernetes operations platform combining container orchestration, CI/CD, monitoring, automatic workload recovery and intelligent troubleshooting.**

<div align="center">

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Amazon EKS](https://img.shields.io/badge/Amazon_EKS-FF9900?style=for-the-badge&logo=amazoneks&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)

</div>

<details>
<summary><b>☸️ Click to explore OpsPilot</b></summary>

<br/>

### 🎯 Problem

Running microservices in Kubernetes requires more than simply creating Pods.

Teams must be able to:

- Deploy applications automatically
- Detect failures
- Recover workloads
- Monitor infrastructure
- Understand Kubernetes errors quickly

### 💡 Solution

**OpsPilot** deploys containerized microservices on Amazon EKS with CI/CD, Kubernetes self-healing, Prometheus/Grafana monitoring and automated troubleshooting assistance.

### 🏗️ Architecture

```mermaid
flowchart TD

    DEV["👨‍💻 Developer"] --> GH["GitHub"]

    GH --> ACTIONS["⚙️ GitHub Actions"]

    ACTIONS --> BUILD["🐳 Docker Build"]

    BUILD --> ECR["📦 Amazon ECR"]

    ECR --> EKS["☸️ Amazon EKS"]

    EKS --> DEP["Kubernetes Deployments"]

    DEP --> PODS["Application Pods"]

    PODS --> PROM["📈 Prometheus"]

    PROM --> GRAF["📊 Grafana"]

    PODS --> OPS["🤖 OpsPilot Diagnostic Engine"]

    OPS --> DIAG["Troubleshooting Suggestions"]
```

### 🧩 Microservices

```text
                    ┌─────────────────┐
                    │     Frontend    │
                    │      Nginx      │
                    └────────┬────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
              ▼              ▼              ▼
        Auth Service    Task Service    Order Service
          FastAPI          API              API
```

### ⚙️ CI/CD Flow

```text
Developer
    │
    ▼
git push
    │
    ▼
GitHub Actions
    │
    ├── Build Docker Image
    │
    └── Push Image
    │
    ▼
Amazon ECR
    │
    ▼
Amazon EKS
```

### ❤️ Kubernetes Self-Healing

Suppose the desired state is:

```text
Desired Pods = 3
```

One Pod crashes:

```text
Current Healthy Pods = 2
```

Kubernetes compares:

```text
Desired State = 3
Actual State  = 2
```

The ReplicaSet controller creates another Pod:

```text
2 Pods
   ↓
ReplicaSet detects difference
   ↓
New Pod created
   ↓
3 Pods running again
```

### 📊 Monitoring

Prometheus collects information including:

- CPU utilization
- Memory usage
- Pod availability
- Pod restart count
- Application metrics

Grafana provides visualization through dashboards.

### 🤖 Troubleshooting Component

The diagnostic component uses the **Kubernetes Python SDK** to inspect workload state.

It can analyze conditions including:

```text
CrashLoopBackOff
ImagePullBackOff
Pending
ContainerCreating
Pod failures
Restart loops
```

and provide troubleshooting guidance based on the detected state.

Example:

```text
Detected:
ImagePullBackOff

Possible checks:
→ Verify image name
→ Verify image tag
→ Verify ECR authentication
→ Verify imagePullSecrets / IAM configuration
```

### 🧰 Technologies

`AWS EKS`
`Amazon ECR`
`Docker`
`Kubernetes`
`GitHub Actions`
`Prometheus`
`Grafana`
`FastAPI`
`Nginx`
`Python`
`Kubernetes Python SDK`

### 🎯 Skills Demonstrated

- Kubernetes architecture
- AWS EKS
- Containerization
- Microservices
- CI/CD
- Monitoring
- Kubernetes troubleshooting
- Self-healing workloads
- Python automation
- Cloud-native application deployment

</details>

---

# 🔐 03 — Production-Grade DevSecOps Cloud Platform

> **Secure cloud-native application delivery using Infrastructure as Code, CI/CD, GitOps, Kubernetes and observability.**

<div align="center">

![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=for-the-badge&logo=terraform&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-FE733A?style=for-the-badge&logo=argo&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)

</div>

<details>
<summary><b>🔐 Click to explore the DevSecOps platform</b></summary>

<br/>

### 🎯 Objective

Design a production-style DevSecOps workflow where infrastructure, security and application delivery are automated.

### 🏗️ Architecture

```mermaid
flowchart TD

    DEV["👨‍💻 Developer"] --> GH["GitHub"]

    GH --> CI["⚙️ GitHub Actions"]

    CI --> TEST["🧪 Tests"]
    CI --> SECURITY["🔐 Security Scan"]
    CI --> BUILD["🐳 Docker Build"]

    TEST --> BUILD
    SECURITY --> BUILD

    BUILD --> ECR["📦 Amazon ECR"]

    ECR --> ARGO["🔄 ArgoCD"]

    ARGO --> EKS["☸️ Amazon EKS"]

    EKS --> HELM["⛵ Helm"]

    HELM --> ALB["🌐 ALB Ingress"]

    ALB --> SERVICE["Kubernetes Service"]

    SERVICE --> PODS["Application Pods"]

    SECRETS["🔑 AWS Secrets Manager"] --> IRSA["IAM / IRSA"]

    IRSA --> PODS

    PODS --> PROM["📈 Prometheus"]

    PROM --> GRAFANA["📊 Grafana"]
```

### 🚀 Delivery Flow

```text
CODE
 │
 ▼
GITHUB
 │
 ▼
CI / TEST
 │
 ▼
SECURITY
 │
 ▼
DOCKER
 │
 ▼
ECR
 │
 ▼
ARGOCD
 │
 ▼
EKS
 │
 ▼
MONITORING
```

### 🔐 Security Concepts

- IAM least privilege
- IRSA
- AWS Secrets Manager
- Container security scanning
- CI/CD security gates
- Private workloads
- Infrastructure as Code

### 🧰 Technologies

`AWS`
`Terraform`
`Docker`
`Kubernetes`
`Amazon EKS`
`Amazon ECR`
`GitHub Actions`
`ArgoCD`
`Helm`
`Prometheus`
`Grafana`

</details>

---

# 🪙 04 — Gold & Silver Price Monitoring System

> **Serverless AWS automation that collects precious-metal prices, stores historical records, compares daily changes and automatically emails reports.**

<div align="center">

![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?style=for-the-badge&logo=awslambda&logoColor=white)
![DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?style=for-the-badge&logo=amazondynamodb&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)

</div>

<details>
<summary><b>🪙 Click to explore the serverless monitoring system</b></summary>

<br/>

### 🎯 Problem

Tracking daily Gold and Silver prices manually makes it difficult to immediately identify price movements and maintain historical records.

### 💡 Solution

I built an automated serverless pipeline that:

1. Fetches market prices
2. Retrieves the previous day's data
3. Calculates the difference
4. Stores today's data
5. Generates an HTML report
6. Emails the report automatically

### 🏗️ Architecture

```mermaid
flowchart TD

    EB["⏰ EventBridge"] --> L["⚡ AWS Lambda"]

    L --> API["🌐 Gold / Silver API"]

    API --> COMPARE["📊 Price Comparison"]

    DB["🗄️ DynamoDB"] --> COMPARE

    COMPARE --> SAVE["💾 Store Today's Price"]

    SAVE --> DB

    COMPARE --> HTML["📄 HTML Report"]

    HTML --> SES["📧 Amazon SES"]

    SES --> USER["Email Notification"]
```

### 🔄 Processing Flow

```text
EventBridge
     │
     ▼
Lambda
     │
     ▼
External Price API
     │
     ▼
Read Previous Price
     │
     ▼
Compare Values
     │
     ▼
Store Today's Data
     │
     ▼
Generate HTML Report
     │
     ▼
SES Email
```

### 📊 Values Processed

- Gold — 1 gram
- Gold — 8 grams
- Silver — 1 gram

Example comparison:

```text
Today's Price      ₹X
Yesterday's Price  ₹Y
                    │
                    ▼
Difference          ₹X - ₹Y
                    │
                    ▼
Increase / Decrease
```

### 🧰 Technologies

`AWS Lambda`
`Amazon DynamoDB`
`Amazon SES`
`Amazon EventBridge`
`Amazon CloudWatch`
`Python`
`Boto3`
`urllib3`
`REST API`

### 🎯 Skills Demonstrated

- Serverless architecture
- Lambda
- DynamoDB
- REST API integration
- Python automation
- Event-driven systems
- Data persistence
- Automated reporting
- Email notifications

</details>

---

# ❤️ 05 — IoT Health Monitoring System

> **Sensor-based IoT system designed to capture and process health and motion information using an ESP32.**

<div align="center">

![Arduino](https://img.shields.io/badge/Arduino-00979D?style=for-the-badge&logo=arduino&logoColor=white)
![C](https://img.shields.io/badge/Embedded_C-A8B9CC?style=for-the-badge&logo=c&logoColor=black)
![IoT](https://img.shields.io/badge/IoT-Embedded_Systems-blue?style=for-the-badge)

</div>

<details>
<summary><b>❤️ Click to explore the IoT system</b></summary>

<br/>

### 🎯 Objective

Build an embedded monitoring system capable of collecting health and motion-related sensor data in real time.

### 🏗️ Architecture

```mermaid
flowchart LR

    TEMP["🌡️ DS18B20"] --> ESP["ESP32"]
    HEART["❤️ MAX30102"] --> ESP
    MOTION["🏃 MPU6050"] --> ESP

    ESP --> PROCESS["⚙️ Process Sensor Data"]

    PROCESS --> OUTPUT["📊 Display / Transmit Results"]
```

### 🔬 Sensors

#### 🌡️ DS18B20

Used for:

```text
Body Temperature
```

#### ❤️ MAX30102

Used for:

```text
Heart Rate
SpO₂
```

#### 🏃 MPU6050

Used for:

```text
Motion Detection
Fall Detection
```

### ⚙️ Data Flow

```text
Sensors
   │
   ▼
ESP32
   │
   ▼
Read Raw Values
   │
   ▼
Process Sensor Data
   │
   ▼
Generate Measurements
   │
   ▼
Display / Transmit Results
```

### 🧰 Technologies

`ESP32`
`DS18B20`
`MAX30102`
`MPU6050`
`Arduino IDE`
`Embedded C`

### 🎯 Skills Demonstrated

- Embedded systems
- IoT architecture
- Sensor integration
- Microcontroller programming
- Hardware/software integration
- Real-time data acquisition

</details>

---

# 🧠 What These Projects Demonstrate

<div align="center">

| ☁️ Cloud | ⚙️ DevOps | 🐍 Automation | 🔐 Security | 📊 Monitoring |
|---|---|---|---|---|
| AWS | CI/CD | Python | IAM | Prometheus |
| Serverless | GitHub Actions | Boto3 | IRSA | Grafana |
| EKS | Docker | API Integration | Secrets | CloudWatch |
| DynamoDB | Kubernetes | Event Automation | DevSecOps | Metrics |

</div>

---

# 🏗️ Engineering Domains

```mermaid
mindmap
  root((Harshith))
    Cloud
      AWS
      Serverless
      EKS
      Networking
    DevOps
      CI/CD
      Docker
      Kubernetes
      GitOps
    Infrastructure
      Terraform
      IaC
      Automation
    Programming
      Python
      Bash
      Boto3
    Observability
      Prometheus
      Grafana
      CloudWatch
    Security
      IAM
      IRSA
      Secrets
      DevSecOps
    IoT
      ESP32
      Sensors
      Embedded C
```

---

# ⚙️ Engineering Practices

| Area | Practice |
|---|---|
| 🏗️ Infrastructure | Infrastructure as Code |
| ☁️ Cloud | AWS architecture |
| 🐍 Automation | Python & Boto3 |
| 🐳 Containers | Docker |
| ☸️ Orchestration | Kubernetes |
| 🔁 CI/CD | Automated build and delivery |
| 🔄 GitOps | Declarative deployments |
| 🔐 Security | Least privilege IAM |
| 🔑 Secrets | External secrets management |
| ❤️ Reliability | Kubernetes self-healing & probes |
| 📊 Observability | Metrics and dashboards |
| 💰 FinOps | Cloud cost optimization |
| ⚡ Serverless | Event-driven AWS architectures |
| 📝 Documentation | Architecture and implementation documentation |

---

## 🎯 Project Focus

<div align="center">

```text
                    HARSHITH'S ENGINEERING PORTFOLIO

                              ☁️ AWS
                                │
                ┌───────────────┼───────────────┐
                │               │               │
                ▼               ▼               ▼
            DEVOPS          SERVERLESS        FINOPS
                │               │               │
                ▼               ▼               ▼
         Kubernetes/EKS      Lambda        Cost Optimizer
                │               │
                ▼               ▼
           CI/CD/GitOps      DynamoDB
                │
                ▼
         Monitoring/Security

                     + Python Automation

                     + IoT / Embedded
```

</div>
