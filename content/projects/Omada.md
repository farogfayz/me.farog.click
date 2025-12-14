---
title: "Secure Wi-Fi Authentication Using Omada, FreeRADIUS, and MySQL"
description: "design and implementation of a secure enterprise Wi-Fi authentication system"
draft: false
tags: ["Linux", "Wifi", "FreeRADIUS", "MariaDB", "Omada"]
showToc: true
weight: 200
cover:
    image: "/projects/Omada.png"
---

## Project Overview
This project demonstrates the design and implementation of a **secure enterprise Wi-Fi authentication system** using **TP-Link Omada**, **FreeRADIUS**, and a **MySQL database**.

The goal was to provide **centralized user authentication**, improve **network security**, and enable **scalable user management** for an academic or enterprise environment.

The system uses **EAP (802.1X)** authentication, allowing users to securely access the wireless network using individual credentials stored in a backend SQL database.

---

## Architecture & Workflow

### Omada Access Points
- Provide wireless connectivity to users  
- Forward authentication requests using **EAP over RADIUS**  
- Do not store user credentials locally, improving security  

### Omada Controller
- Centralized management of access points and SSIDs  
- Configured an **Enterprise WPA2/WPA3 SSID** using **802.1X**  
- Integrated with an external RADIUS server (**FreeRADIUS**)  
- Ensures consistent policy enforcement across all APs  

### FreeRADIUS Server
- Acts as the **authentication and authorization server**  
- Handles EAP authentication (**EAP-PEAP / MS-CHAPv2**)  
- Validates user credentials against a MySQL database  
- Sends **Access-Accept / Access-Reject** responses to Omada  
- Logs authentication and accounting events  

### MySQL Database
- Stores user credentials and policies (`radcheck`, `radreply`)  
- Stores session and accounting data (`radacct`)  
- Enables easy user provisioning, revocation, and auditing  
- Supports future integration with external systems (LDAP, portals, ERP)  

---

## Authentication Flow
1. A user connects to the secure Wi-Fi SSID  
2. The Omada Access Point forwards the authentication request to FreeRADIUS  
3. FreeRADIUS performs EAP authentication  
4. User credentials are verified against the MySQL database  

**If authentication is successful:**
- Access is granted  
- Accounting data is logged  

**If authentication fails:**
- Access is denied  
- Event is logged for auditing and troubleshooting  

---

## Key Features Implemented
- ✔ Enterprise-grade Wi-Fi security (**802.1X / EAP**)  
- ✔ Centralized authentication using **FreeRADIUS**  
- ✔ SQL-based user management  
- ✔ Per-user access control  
- ✔ Authentication and accounting logging  
- ✔ Scalable design suitable for campuses or enterprises  
- ✔ Vendor-agnostic RADIUS backend  

---

## Technologies Used
- **TP-Link Omada** (Controller & Access Points)  
- **FreeRADIUS**  
- **MySQL / MariaDB**  
- **EAP-PEAP / MS-CHAPv2**  
- **Linux Server** (Debian / Ubuntu)  

---

## Use Case
This solution is suitable for:
- Universities and campuses  
- Enterprises with multiple departments  
- Secure staff and student Wi-Fi networks  
- Environments requiring auditing and accountability  

---

## What This Project Demonstrates
- Strong understanding of **802.1X and RADIUS authentication**  
- Practical experience integrating **network infrastructure with backend services**  
- Ability to design **secure, scalable, real-world network solutions**  
- Hands-on knowledge of **FreeRADIUS internals and SQL integration**  
