# Ansible Role: snmpv3

This Ansible role installs and configures **SNMPv3** on a Linux host (VM, bare metal, or container) to act as an **SNMP target** (for example, a switch or router) that can be securely monitored by systems like **Prometheus SNMP Exporter** or **Nagios**.

The role:
- Installs SNMP packages
- Creates an SNMPv3 user with `authPriv`
- Configures `snmpd`
- Enables and starts the SNMP service
- Optionally opens UDP port 161 in the firewall

---

## ✅ Supported Platforms

- Ubuntu 20.04+
- Debian-based systems
- Incus/LXD containers
- Lab or production environments

---

## 📦 Requirements

- SSH access to the target host
- `sudo` privileges
- Ansible ≥ 2.12
- Firewall management via `ufw` (optional)

---

## 🔧 Role Variables

All variables are configurable and should ideally be protected using **Ansible Vault**.

### `roles/snmpv3/vars/main.yml`

| Variable | Description | Example |
|-------|------------|--------|
| `snmp_user` | SNMPv3 username | `Hero` |
| `snmp_auth_protocol` | Authentication protocol | `SHA` |
| `snmp_auth_password` | Authentication password | `Hero12345` |
| `snmp_priv_protocol` | Privacy protocol | `AES` |
| `snmp_priv_password` | Privacy password | `Hero12345` |
| `sys_location` | System location string | `Incus Test Lab` |
| `sys_contact` | System contact email | `anuj@example.com` |

---

## 📁 Inventory Example

```ini
[snmp_targets]
snmp-target ansible_host=10.12.242.150 ansible_user=ubuntu
