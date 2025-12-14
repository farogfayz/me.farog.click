---
title: "Network Automation with Ansible"
description: "A modern and scalable solution to automate switch and router configurations using Ansible."
draft: false
tags: ["Ansible", "Network Automation", "DevOps", "Cisco", "Linux", "Infrastructure as Code"]
showToc: true
weight: 203
cover:
  image: "/projects/ansible.png"
---

# Network Automation with Ansible

## Overview
This project showcases how to use **Ansible**, an open-source automation tool, to manage network devices like switches and routers. It automates repetitive configurations such as VLAN creation, interface assignment, and ACL deployment across multiple devices.

---

## Why Ansible for Networking?

- **Agentless:** Uses SSH or API—no software needed on devices.
- **Repeatable:** Write once, apply many times.
- **Multi-Vendor Support:** Works with Cisco, Juniper, Arista, and more.
- **Audit-Friendly:** YAML playbooks act as documentation.
- **Scalable:** Easily manage hundreds of devices across sites.

---

## Core Features

1. **Inventory Management:** Define all network devices in one file.
2. **VLAN Automation:** Automatically create and assign VLANs.
3. **Interface Configuration:** Apply port descriptions, switchport modes, and more.
4. **Access Control Lists (ACLs):** Deploy security policies across routers and firewalls.
5. **Validation & Logging:** Confirm changes and store output for auditing.

---

## Architecture

- **Ansible Control Node:** Central system where playbooks run.
- **Inventory File:** YAML file listing all network devices with variables.
- **Playbooks & Roles:** Reusable automation code for common network tasks.
- **Network Devices:** Cisco or other vendor switches/routers accessed via SSH or API.

---

## Setup Summary

1. Created an inventory file with device IPs, models, and credentials.
2. Wrote modular playbooks for VLANs, interfaces, and ACLs.
3. Used `ansible.netcommon` and `cisco.ios` collections for tasks.
4. Executed playbooks to push configs and validate status.
5. Logged results and verified with `show` commands.

---

## Use Cases

- **Network Engineers:** Automate mass device configurations.
- **System Admins:** Reduce manual switch setup time.
- **DevOps Teams:** Integrate networking into CI/CD pipelines.
- **Educational Labs:** Create reproducible topologies in GNS3 or EVE-NG.

---

## Resources
- 🌐 [Ansible Networking Docs](http://docs.ansible.com/network/)  
- 📦 [Cisco IOS Collection](http://galaxy.ansible.com/cisco/ios)  
- 💻 [GitHub Sample Repo](http://github.com/ansible-network)

---

## Future Enhancements
- Add backup and rollback features.
- Integrate with NetBox for dynamic inventory.
- Deploy configuration drift detection.

