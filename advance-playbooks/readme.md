# Advanced Ansible Playbooks

This directory contains more advanced Ansible playbooks that extend beyond basic ad-hoc commands and simple automation tasks.

These playbooks demonstrate real-world automation scenarios including service deployment, system configuration, and multi-host orchestration.

---

## Purpose

The goal of this section is to practice production-style infrastructure automation patterns such as:

- Multi-host orchestration
- Service deployment
- System baseline configuration
- User and access management
- Infrastructure standardization

---

## Playbooks Included

### multi-tier-deployment.yml
Simulates deployment of a multi-tier application stack including web servers and backend services.

### nginx-webserver.yml
Automates installation and configuration of an NGINX web server.

Tasks may include:

- Installing NGINX
- Starting and enabling the service
- Deploying configuration templates

---

### system-hardening.yml
Applies baseline security configurations to Linux hosts.

Examples:

- Disable unused services
- Enforce SSH configuration
- Update packages

---

### user-management.yml
Automates system user provisioning.

Examples:

- Create users
- Configure SSH access
- Manage sudo permissions

---

### package-baseline.yml
Ensures required packages are installed across all hosts.

Examples:

- Monitoring tools
- Networking utilities
- Standard OS packages

---

## Running a Playbook

Example execution:

```bash
ansible-playbook playbooks/nginx-webserver.yml
