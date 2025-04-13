Here’s a sample **README.md** for your self-managed OKD cluster project on AWS using Terraform, Ansible, and Vault:

---

# 🧑‍💻 Self-Managed OKD Cluster on AWS with Terraform, Ansible & Vault

## 📌 Overview

This project sets up a **self-managed OKD (OpenShift Origin) cluster** on **AWS EC2 instances** using a fully automated infrastructure pipeline. It leverages:

- **Terraform** for infrastructure provisioning
- **Ansible** for system and OKD configuration
- **HashiCorp Vault** for secret management

The goal is to demonstrate a production-style deployment of an OpenShift-compatible Kubernetes distribution using open-source tools and cloud-native practices.

---

## 🏗 Architecture

- **EC2 Instances** (RHEL/CentOS/Rocky preferred):
  - 1 Bootstrap node
  - 1 Master (control plane)
  - 2 Worker nodes
- **Networking**:
  - VPC with subnets, routing, security groups
- **Terraform**:
  - Manages EC2, IAM, VPC, SGs
- **Ansible**:
  - Installs dependencies, sets up OKD nodes
- **Vault**:
  - Manages TLS certs, kubeadmin credentials, secrets

---

## 🔧 Tools Used

| Tool | Purpose |
|------|---------|
| Terraform | Provision AWS infrastructure |
| Ansible | Automate OKD setup and node configuration |
| Vault | Secret management for Kubernetes and cluster access |
| OKD | OpenShift-compatible Kubernetes cluster |
| AWS | Cloud infrastructure provider |

---

## 🚀 Getting Started

### 1. Clone Repository

```bash
git clone https://github.com/manupanand-freelance-developer/selfmanaged-okd-openshift-cluster-prjt-15-2025.git
cd selfmanaged-okd-openshift-cluster-prjt-15-2025
```

### 2. Configure Terraform

```bash
cd terraform
terraform init -backend-config=env-dev/state.tfvars
terraform apply -var-file=env-dev/main.tfvars -auto-approve
```

This will create:
- VPC
- EC2 instances
- SSH key pairs
- Security groups

### 3. Set up Vault (Optional but recommended)

- Start Vault on a local machine or EC2
- Store secrets (certs, tokens)
- prefer vault operations using github actions
or 
```bash
vault kv put secret/okd/kubeadmin-password password=<strongpassword>
```

### 4. Run Ansible Playbooks
by default terraform initate user script while provisioning which will ensure dependencies installation

or 

```bash
cd ansible
ansible-playbook playbook.yaml -e role_name
```

This sets up:
- Podman/docker
- CRI-O
- Required packages
- OKD installation

---

## ✅ Features

- AWS-native provisioning
- Full automation using IaC and config management
- Self-managed Kubernetes with OKD
- Vault integration for security

---

## 📊 SLO Considerations

- **99.9% Uptime Target**
- **15m ETTD** with Prometheus + Alertmanager
- **4h ETTR** planned via Ansible re-runs

---

## 🔐 Security Practices

- Secrets managed via Vault
- Secure SSH access using AWS key pairs
- Role-based access for OKD users

---

## 💡 Future Enhancements

- Add monitoring (Prometheus, Grafana)
- CI/CD pipeline for application deployment
- Auto-scaling worker nodes
- Let’s Encrypt cert automation

---

## 📎 License

GNU GPLv3 © 2025 Manu Panand
---

