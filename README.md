# azure-secure-network-monitoring
Designed and deployed a secure Azure virtual network...
# 🔐 Azure Secure Network with Monitoring & Alerts

## 📌 Overview
This project demonstrates how to design, deploy, and operate a secure Azure network environment using subnet segmentation, Network Security Groups (NSGs), and proactive monitoring with Azure Monitor and Log Analytics.

The goal is to simulate real-world Azure infrastructure practices focused on security, observability, and cost control—core responsibilities of a Junior Cloud Engineer.

---

## 🏗 Architecture

Resource Group
│
├── Virtual Network (10.0.0.0/16)
│ ├── web-subnet (10.0.1.0/24)
│ │ ├── NSG: nsg-web
│ │ └── Linux VM (Ubuntu)
│ │
│ └── management-subnet (10.0.2.0/24)
│ └── NSG: nsg-mgmt
│
├── Log Analytics Workspace
└── Azure Monitor Alerts


---

## 🌐 Network Design
- **Virtual Network:** vnet-secure-prod
- **Address Space:** 10.0.0.0/16

### Subnets
| Subnet | CIDR | Purpose |
|------|------|--------|
| web-subnet | 10.0.1.0/24 | Hosts application workloads |
| management-subnet | 10.0.2.0/24 | Restricted administrative access |

Subnet segmentation limits blast radius and enables granular security controls.

---

## 🔐 Security Controls
### Network Security Groups (NSGs)
NSGs are applied at the subnet level using a default-deny inbound model.

#### nsg-web
- Allow SSH (TCP 22) only from a trusted public IP (/32)
- Deny all other inbound traffic

#### nsg-mgmt
- Allow SSH only from management-subnet
- Prevent unauthorized lateral access

Security principles applied:
- Least privilege
- Explicit allow rules
- Reduced attack surface

---

## 🖥 Compute
- **VM OS:** Ubuntu Server LTS
- **Deployment:** web-subnet
- **VM Size:** Small (cost-efficient)
- **Access:** Public IP used only for testing

In production, access would be handled using Azure Bastion or private endpoints.

---

## 📊 Monitoring & Observability
### Azure Monitor
- VM Insights enabled
- CPU and availability metrics collected

### Log Analytics
- Centralized logging
- Supports troubleshooting and trend analysis

Operational visibility enables proactive detection of failures and performance issues.

---

## 🚨 Alerts
| Alert | Condition | Purpose |
|----|----|----|
| High CPU | > 80% | Detect performance issues |
| VM Availability | VM down | Detect outages |

Alerts notify the operator via email using an Azure Action Group.

---

## ✅ Validation
- Verified SSH access allowed only from authorized IP
- Confirmed blocked access from unauthorized sources
- Triggered CPU alert using stress testing
- Triggered downtime alert by stopping the VM

---

## 💰 Cost Management
- Small VM size selected
- Monitoring scoped to essential metrics
- All resources deployed in a single resource group
- Resource group deleted after testing to prevent unnecessary costs

---

## 🔁 Functional Flow
1. Connection request hits NSG
2. NSG evaluates inbound rules
3. Authorized traffic allowed, others denied
4. VM runs securely inside subnet
5. Azure Monitor collects telemetry
6. Alerts trigger on abnormal conditions
7. Operator is notified and responds

---

## 🎯 Skills Demonstrated
- Azure networking (VNets, subnets, NSGs)
- Cloud security fundamentals
- Linux VM deployment
- Monitoring and alerting
- Incident detection and troubleshooting
- Cost-aware cloud operations

---

## 🧹 Cleanup
All resources were removed by deleting the resource group to prevent ongoing cloud charges.

---

## 🧠 Interview Summary
Designed and deployed a secure Azure network using subnet segmentation and NSGs, then implemented monitoring and alerting with Azure Monitor to maintain operational visibility and reliability.




