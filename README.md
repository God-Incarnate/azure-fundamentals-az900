# 🚀 Microsoft Azure Fundamentals (AZ-900)

**Industrial Internship Report & Hands-on Azure Learning Repository**

![Azure Badge]([https://img.shields.io/badge/Azure-Fundamentals-0078D4](https://drive.google.com/file/d/1LILYcse-h14aZTVJh80s7CfAQHGmLm50/view?usp=drive_link)?style=flat-square&logo=microsoft-azure)
![AZ-900](https://drive.google.com/file/d/1bGJ9ImmD5N2GXDPI7tk1w4H3bRxrmkxa/view?usp=drive_link?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

---

## 📌 Overview

This repository contains detailed notes, concepts, architecture explanations, and practical experiments related to **Microsoft Azure Fundamentals (AZ-900)**.

The project was completed as part of an industrial internship and focuses on understanding:

- ☁️ Cloud Computing Concepts
- 🏗️ Azure Deployment Models
- ⚡ Azure Core Services
- 💾 Storage & Database Services
- 🔐 Azure Security & Identity
- 🛡️ Azure Active Directory & MFA
- 🔑 Azure Key Vault
- 🛠️ Infrastructure as Code (ARM)
- 🌐 IoT Services on Azure
- 🧪 Practical Azure Deployments

---

## 👨‍💻 Author

**Prashant Verma**  
B.Tech CSE  
VIT University Chennai

---

## 📚 Table of Contents

1. [Introduction](#introduction)
2. [Cloud Concepts](#cloud-concepts)
3. [Azure Deployment Models](#azure-deployment-models)
4. [Azure Services Overview](#azure-services-overview)
5. [Compute Services](#compute-services)
6. [Storage Services](#storage-services)
7. [Database Services](#database-services)
8. [Azure Resource Manager](#azure-resource-manager)
9. [IoT Services](#iot-services)
10. [Azure Portal](#azure-portal)
11. [Azure Active Directory](#azure-active-directory)
12. [Security & Compliance](#security--compliance)
13. [Practical Experiments](#practical-experiments)
14. [Key Learnings](#key-learnings)
15. [Future Scope](#future-scope)

---

## 🌍 Introduction

Microsoft Azure is a cloud computing platform offering services such as:

- **Compute** - Virtual Machines, App Services, Containers
- **Storage** - Blob Storage, Disk Storage, File Shares
- **Networking** - Virtual Networks, Load Balancers, VPN Gateway
- **Databases** - SQL Database, Cosmos DB, MySQL
- **Analytics** - Azure Synapse, Data Lake, Stream Analytics
- **AI & ML** - Cognitive Services, Machine Learning
- **Security** - Key Vault, Azure AD, DDoS Protection

Azure enables organizations and developers to build, deploy, and scale applications without managing physical infrastructure.

### Benefits of Azure

The AZ-900 Azure Fundamentals Certification provides foundational knowledge about:
- Cloud Concepts
- Azure Services & Architecture
- Azure Pricing & Governance
- Security & Compliance

---

## ☁️ Cloud Concepts

### What is Cloud Computing?

Cloud computing delivers computing services over the internet, including servers, storage, databases, networking, software, and analytics.

### Advantages of Cloud Computing

| Advantage | Description |
|-----------|-------------|
| **Scalability** | Easily scale resources up or down based on demand |
| **High Availability** | Minimal downtime with redundant systems |
| **Elasticity** | Automatically adjust resources as needed |
| **Cost Optimization** | Pay only for what you use (OPEX) |
| **Global Reach** | Deploy applications worldwide |
| **Security** | Enterprise-grade security features |
| **Disaster Recovery** | Built-in backup and recovery mechanisms |

---

## 🏗️ Types of Cloud Services

### 1. Infrastructure as a Service (IaaS)

Provides virtualized computing resources over the internet.

**Services Include:**
- Virtual Machines
- Storage Services
- Networking Components
- Firewalls & Load Balancers

**Examples:** Azure Virtual Machines, AWS EC2

**When to Use:** When you need maximum control over infrastructure and custom configurations

---

### 2. Platform as a Service (PaaS)

Provides development and deployment environments in the cloud.

**Services Include:**
- Middleware
- Databases
- Development Tools
- Business Intelligence Tools

**Examples:** Azure App Services, Google App Engine

**When to Use:** When you want to focus on application development without managing infrastructure

---

### 3. Software as a Service (SaaS)

Provides ready-to-use software applications accessed via web browser.

**Examples:**
- Microsoft 365
- Gmail
- Google Drive
- Salesforce

**When to Use:** When you need access to applications without installation or maintenance

---

## 🌐 Azure Deployment Models

### 1. Public Cloud

Infrastructure is owned and operated by the cloud provider.

**Benefits:**
- Cost Effective
- Highly Scalable
- Easy Maintenance
- No upfront infrastructure investment

**Use Cases:** Web applications, development/testing, disaster recovery

---

### 2. Private Cloud

Infrastructure is owned and managed internally by the organization.

**Benefits:**
- Better Control
- Higher Security
- Compliance Requirements
- Customization

**Use Cases:** Financial institutions, healthcare, sensitive data processing

---

### 3. Hybrid Cloud

Combination of Public + Private Cloud infrastructure.

**Benefits:**
- Flexibility & Control
- Data Compliance
- Cost Optimization
- Disaster Recovery & Failover

**Use Cases:** Legacy system migration, data sovereignty, burst capacity

---

## 💰 CAPEX vs OPEX

### CAPEX (Capital Expenditure)

**Upfront infrastructure investment** for physical assets.

**Includes:**
- Servers & Hardware
- Data Centers & Real Estate
- Cooling & Power Systems
- Networking Equipment

**Characteristics:**
- High initial cost
- Long-term asset depreciation
- Requires maintenance & upgrades

---

### OPEX (Operational Expenditure)

**Pay-as-you-go cloud model** with recurring costs.

**Includes:**
- Cloud Subscription Fees
- Compute & Storage Usage
- Data Transfer Costs
- Cloud Support Services

**Characteristics:**
- Lower initial investment
- Flexible scaling
- Predictable monthly costs

---

## ⚡ Azure Services Overview

### Compute Services
- Azure Virtual Machines
- Azure Kubernetes Service (AKS)
- Azure Service Fabric
- Azure Batch

### Storage Services
- Azure Blob Storage
- Azure Disk Storage
- Azure File Storage
- Azure Queue Storage
- Azure Table Storage
- Azure Archive Storage

### Database Services
- Azure SQL Database
- Azure Cosmos DB
- Azure Database for MySQL
- Azure Cache for Redis

### Networking Services
- Virtual Networks
- Load Balancers
- Application Gateway
- VPN Gateway

### Security Services
- Azure Active Directory
- Azure Key Vault
- Azure Security Center
- DDoS Protection

---

## ⚡ Compute Services

### Azure Virtual Machines

Create and manage Windows/Linux VMs in Azure.

**Features:**
- Custom CPU/RAM Configuration
- SSD/HDD Storage Support
- Auto-scaling Capabilities
- High Availability Options

**Use Cases:**
- Legacy application hosting
- Development & testing environments
- Custom application requirements

---

### Azure Kubernetes Service (AKS)

Managed Kubernetes platform for container orchestration.

**Benefits:**
- Automatic Container Orchestration
- Scalability & Load Balancing
- High Availability
- Integrated Security
- Auto-scaling Based on Demand

**Use Cases:**
- Microservices architecture
- Cloud-native applications
- CI/CD Pipelines

---

### Azure Service Fabric

Distributed systems platform for microservices and reliable services.

**Features:**
- Microservices Deployment
- Stateful & Stateless Services
- Automatic Scaling
- Self-healing Capabilities

---

### Azure Batch

Run parallel large-scale batch jobs efficiently.

**Use Cases:**
- Data Processing
- Media Rendering
- Scientific Simulations
- Machine Learning Training

---

## 💾 Storage Services

### Azure Blob Storage

Object storage for unstructured data (files of any size).

**Use Cases:**
- Images & Videos
- Backup & Archive Files
- Log Files
- Media Distribution

**Storage Tiers:**
- Hot (Frequently accessed)
- Cool (Infrequently accessed)
- Archive (Long-term retention)

---

### Azure Disk Storage

Persistent block storage for Virtual Machines.

**Types:**
- Standard HDD
- Standard SSD
- Premium SSD

---

### Azure File Storage

Managed cloud file shares accessible via SMB.

**Use Cases:**
- Shared file access
- Application data storage
- Cross-platform file sharing

---

### Azure Queue Storage

Reliable messaging service between applications.

**Use Cases:**
- Asynchronous message processing
- Decoupling application components
- Job queue management

---

### Azure Table Storage

NoSQL key-value store for semi-structured data.

**Use Cases:**
- User profiles
- Device logs
- Session management

---

### Azure Archive Storage

Low-cost long-term storage for rarely accessed data.

**Use Cases:**
- Compliance archiving
- Long-term backups
- Historical data retention

---

## 🗄️ Database Services

### Azure Cosmos DB

Globally distributed NoSQL database service.

**Features:**
- 99.999% Availability SLA
- Low Latency Globally
- Massive Scalability
- Multiple Consistency Models
- Multi-region Replication

**Use Cases:**
- IoT Data
- Real-time Analytics
- Global Applications
- Content Management

---

### Azure SQL Database

Managed relational database service with built-in intelligence.

**Features:**
- Fully Managed Service
- Automatic Backups
- Security & Compliance
- Performance Tuning
- High Availability

**Use Cases:**
- Enterprise Applications
- Traditional RDBMS Workloads
- Business-critical Data

---

### Azure Database for MySQL

Managed MySQL database service in the cloud.

**Features:**
- Automated Backups
- Point-in-time Restore
- High Availability Replicas
- Security Features

---

### Azure Cache for Redis

High-speed distributed caching system.

**Use Cases:**
- Session Caching
- Database Query Caching
- Real-time Data
- Leaderboards & Counters

---

## 🛠️ Azure Resource Manager (ARM)

Infrastructure as Code (IaC) service for Azure resource deployment.

**Key Concepts:**

**Resource Groups:** Logical containers for related resources

**ARM Templates:** JSON files defining infrastructure configuration

**Benefits:**
- Automated Deployment
- Repeatable Infrastructure
- Consistent Configurations
- Version Control Friendly
- Resource Grouping & Management
- Easy Updates & Rollbacks

**Deployment Models:**
- Declarative (desired state)
- Imperative (step-by-step)

---

## 🌐 IoT Services

### IoT Central

Connect, monitor, and manage IoT devices at scale.

**Features:**
- Device Management
- Rules & Actions
- Data Visualization
- Mobile App Integration

---

### IoT Hub

Secure, scalable communication between IoT devices and cloud.

**Features:**
- Bidirectional Communication
- Device Authentication
- Message Routing
- Event Processing

---

### IoT Edge

Process data locally on edge devices (on-premises).

**Benefits:**
- Reduced Latency
- Lower Bandwidth Usage
- Offline Capability
- Local Processing

---

## 🖥️ Azure Portal

Web-based interface to manage all Azure services.

**Key Features:**
- Deploy & Manage Resources
- Monitor Applications & Performance
- Manage Infrastructure & Settings
- Billing & Cost Analysis
- Resource Navigation & Search

**Navigation:**
- Home Dashboard
- Resource Groups
- All Resources
- Recent Resources
- Marketplace

---

## 🔐 Azure Active Directory (Azure AD)

Cloud identity and access management service.

**Core Features:**
- Single Sign-On (SSO)
- User Authentication & Authorization
- Identity Protection
- Conditional Access
- Multi-Factor Authentication

**Use Cases:**
- Enterprise Identity Management
- Application Access Control
- B2B & B2C Scenarios
- Device Management

**Key Concepts:**
- Tenants (Organizations)
- Users & Groups
- Roles & Permissions
- Applications & Service Principals

---

## 🛡️ Multi-Factor Authentication (MFA)

Adds additional security layers beyond username/password.

**Authentication Methods:**
- One-Time Password (OTP)
- Authenticator Apps (Microsoft Authenticator, Google Authenticator)
- SMS Verification
- Biometric Verification (Fingerprint, Face Recognition)
- Phone Call Verification

**Benefits:**
- Enhanced Security
- Compliance Requirements
- Reduced Account Takeover Risk
- User Accountability

---

## 🔑 Azure Key Vault

Securely stores and manages secrets, keys, and certificates.

**Capabilities:**
- **Secrets Management** - Passwords, connection strings, API keys
- **Certificate Management** - SSL/TLS certificates
- **Encryption Keys** - Data encryption keys
- **Hardware Security Modules (HSM)** - FIPS 140-2 compliance

**Benefits:**
- Centralized Secret Management
- Access Control & Auditing
- Automatic Rotation
- Compliance & Governance
- Integration with Azure Services

---

## 🧪 Practical Experiments

### 1️⃣ Azure Virtual Machine Deployment

**Objective:** Create and configure a virtual machine in Azure

**Steps:**

1. Open Azure Portal
2. Navigate to Virtual Machines
3. Click "Create" → "Virtual Machine"
4. Configure settings:
   - **Resource Group:** Create new or select existing
   - **VM Name:** Provide unique name
   - **Region:** Select nearest region
   - **Availability Options:** Zone redundancy if needed
   - **Image:** Select OS (Windows/Linux)
   - **Size:** Choose CPU/RAM (Standard_B2s recommended for testing)
   - **Authentication:** Password or SSH keys
   - **Networking:** Virtual Network, Subnet, NSG rules
5. Review and Create
6. Wait for deployment (2-5 minutes)
7. Connect using RDP (Windows) or SSH (Linux)

**Expected Output:** Running VM accessible via RDP/SSH

---

### 2️⃣ Azure Web App Deployment

**Objective:** Deploy a web application to Azure App Service

**Steps:**

1. Open Azure Portal
2. Navigate to App Services
3. Click "Create" → "Web App"
4. Configure settings:
   - **App Name:** Unique name (becomes URL)
   - **Resource Group:** Create or select
   - **Runtime Stack:** Select technology (Node.js, Python, .NET, etc.)
   - **Region:** Choose nearest region
   - **Pricing Tier:** Select plan (Free tier available)
5. Review and Create
6. Deploy application:
   - Via Git/GitHub
   - Via zip file upload
   - Via Visual Studio
7. Access via generated URL: `https://appname.azurewebsites.net`

**Expected Output:** Web app running at public URL

---

### 3️⃣ Azure Blob Storage Setup

**Objective:** Create and manage blob storage

**Steps:**

1. Create Storage Account
   - Open Azure Portal
   - Search "Storage Accounts"
   - Click Create
   - Configure: Name, Region, Performance, Replication
2. Create Blob Container
   - Navigate to Storage Account
   - Select "Containers"
   - Click "+ Container"
   - Set name and access level
3. Upload Files
   - Select container
   - Click "Upload"
   - Select files from local machine
4. Monitor Storage
   - View metrics (used capacity, requests)
   - Set lifecycle policies
   - Configure access controls

**Expected Output:** Files accessible via blob URL with proper access controls

---

### 4️⃣ Azure SQL Database Setup

**Objective:** Create and query an Azure SQL Database

**Steps:**

1. Create SQL Database
   - Open Azure Portal
   - Search "SQL Databases"
   - Click Create
   - Configure: Database name, Server, Pricing tier
2. Create SQL Server (if new)
   - Set server name
   - Configure admin credentials
   - Configure firewall (allow your IP)
3. Deploy Database
   - Review configuration
   - Click Create
   - Wait for provisioning (2-3 minutes)
4. Connect & Query
   - Select "Query Editor"
   - Login with admin credentials
   - Execute SQL queries:
     ```sql
     CREATE TABLE Users (
       UserID INT PRIMARY KEY,
       UserName VARCHAR(100),
       Email VARCHAR(100)
     );
     
     INSERT INTO Users VALUES (1, 'Prashant', 'prashant@example.com');
     SELECT * FROM Users;
     ```

**Expected Output:** Database with sample tables and data

---

## 📊 Architecture Diagrams

### Basic Azure Architecture Flow

```
┌─────────────────────────────────────────────────────────────┐
│                      Azure Portal                            │
└─────────────────────────────────────────────────────────────┘
         │
         ├─────────────────────────────────────────┐
         │                                         │
    ┌────▼─────┐                          ┌────────▼──────┐
    │ Compute  │                          │   Storage     │
    │ Services │                          │   Services    │
    ├──────────┤                          ├───────────────┤
    │• VMs     │                          │• Blob Storage │
    │• AKS     │                          │• Disk Storage │
    │• App Srv │                          │• File Share   │
    └──────────┘                          └───────────────┘
         │                                     │
         └──────────────┬──────────────────────┘
                        │
              ┌─────────▼──────────┐
              │  Resource Manager  │
              │  (ARM Templates)   │
              └────────────────────┘
                        │
         ┌──────────────┼──────────────┐
         │              │              │
    ┌────▼────┐  ┌─────▼─────┐  ┌────▼─────┐
    │ Database │  │  Security │  │ Networking│
    │ Services │  │  Services │  │ Services  │
    │          │  │           │  │           │
    │• SQL DB  │  │• Azure AD │  │• Vnet    │
    │• Cosmos  │  │• Key Vault│  │• LB      │
    │• Redis   │  │• MFA      │  │• VPN     │
    └──────────┘  └───────────┘  └──────────┘
```

---

## 📈 Skills Gained

- ✅ Cloud Computing Fundamentals
- ✅ Azure Service Management
- ✅ Virtual Machine Deployment & Configuration
- ✅ Blob Storage & File Management
- ✅ SQL Database Creation & Querying
- ✅ Identity Management (Azure AD)
- ✅ Cloud Security & Compliance
- ✅ Infrastructure as Code (ARM Templates)
- ✅ Web Application Deployment
- ✅ IoT Services Configuration
- ✅ Cost Optimization & Governance

---

## 🔥 Key Learnings

1. **Cloud computing reduces infrastructure cost** - OPEX model vs traditional CAPEX
2. **Azure provides scalable and secure services** - Global infrastructure with compliance certifications
3. **Infrastructure can be automated using ARM** - Infrastructure as Code for consistency
4. **Cloud services improve deployment speed and flexibility** - Minutes vs weeks for traditional IT
5. **Security and identity management are critical** - Azure AD, MFA, Key Vault are essential
6. **Hybrid models provide flexibility** - Combine public and private cloud based on needs
7. **Different service models (IaaS/PaaS/SaaS) serve different needs** - Choose based on control requirements
8. **Monitoring and governance are important** - Cost optimization and compliance tracking

---

## 📌 Future Scope

- 🚀 **Azure DevOps** - CI/CD pipelines, Git, Release management
- 🤖 **AI & Machine Learning on Azure** - Cognitive Services, ML Studio, AutoML
- 🐳 **Kubernetes & Containers** - Deep dive into AKS, Docker, container registries
- 🔧 **Serverless Computing** - Azure Functions, Logic Apps, Event Grid
- 🛡️ **Cloud Security Engineering** - Advanced security postures, threat detection
- 🌍 **Multi-cloud Architectures** - Hybrid multi-cloud strategies
- 📊 **Advanced Analytics** - Synapse Analytics, Data Lake, Databricks
- 🎯 **Advanced IoT Solutions** - Edge computing, real-time processing

---

## 🏁 Conclusion

Microsoft Azure provides a powerful cloud ecosystem for modern applications and enterprise solutions. Its flexibility, scalability, security, and global infrastructure make it one of the leading cloud platforms in the industry.

### Key Takeaways

This learning journey covered:
- Core Cloud Concepts & Service Models
- Azure Architecture & Services
- Cloud Deployment Models (Public, Private, Hybrid)
- Security & Identity Management
- Storage & Database Services
- Real-world Azure Hands-on Experiments
- Infrastructure as Code with ARM Templates
- IoT & Emerging Technologies

### Why Azure Matters

1. **Enterprise Adoption** - Trusted by 95% of Fortune 500 companies
2. **Global Presence** - 60+ data center regions worldwide
3. **Compliance** - Meets global regulatory requirements (GDPR, HIPAA, ISO)
4. **Integration** - Seamlessly integrates with Microsoft ecosystem
5. **Innovation** - Continuously evolving with AI, ML, and advanced services

---

## 📚 Additional Resources

- [Microsoft Learn - Azure Fundamentals](https://learn.microsoft.com/en-us/training/paths/azure-fundamentals/)
- [AZ-900 Exam Guide](https://learn.microsoft.com/en-us/certifications/exams/az-900)
- [Azure Documentation](https://docs.microsoft.com/azure/)
- [Azure Architecture Center](https://docs.microsoft.com/en-us/azure/architecture/)

---

## 📞 Support & Questions

For questions or clarifications:
- 📧 Contact: prashant.verma@example.com
- 🐙 GitHub Issues: [Create an Issue](https://github.com/God-Incarnate/azure-fundamentals-az900/issues)
- 💬 Discussions: [Join Discussion](https://github.com/God-Incarnate/azure-fundamentals-az900/discussions)

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

**⭐ If this repository helped you, please consider giving it a star!**

**Last Updated:** May 2026  
**Status:** ✅ Complete & Ready for Learning
