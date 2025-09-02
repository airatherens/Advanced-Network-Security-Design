# Advanced Network Security Design

Palo Alto Networks + VMware Workstation Security Lab (ITSC-350)  
Globex Corporation – Group 6 – Calgary HQ  
Contributors: Dylan Yee, Amrit Kaur Dhiman, Aira Therens  

---

## 📖 Overview

This project demonstrates the deployment and configuration of a **Palo Alto VM-50 firewall**, Virtual Router, DMZ server, and client machines inside **VMware Workstation**.  
It follows a layered security approach with **Internal**, **DMZ**, **External**, and **Management** zones.  

**Objectives:**
- Deploy Palo Alto Firewall (v10.0) with VMware Workstation
- Configure Internal, External, DMZ, and Management zones
- Apply advanced **security policies** (file blocking, data filtering, geo-blocking)
- Deploy **NGINX** and **MineMeld** containers
- Centralize **Syslog monitoring & forwarding**
- Demonstrate NAT, routing, and reconnaissance protection
- Propose a **cloud disaster recovery (DR)** strategy

---

## 🏗️ Network Topology

![Topology Diagram](assets/topology-diagram.png)

**Zones:**
- **External Zone** → Internet connection  
- **DMZ Zone** → Public-facing services (NGINX, Syslog Server)  
- **Internal Zone** → Workstations  
- **Management Zone** → Firewall admin access (192.168.1.254)  

---

## ⚙️ Key Configurations

### Security Policies
- **Data Filtering:** Block SSNs using regex pattern match  
- **File Blocking:** Block PDF uploads/downloads  
- **Block List:** Deny access to specific domains (via block-list.txt)  
- **International Geo-Blocking:** Deny traffic from Cuba, Bahamas, Chad  
- **Zone Protection:** Flood & reconnaissance protection enabled on External + DMZ  

### Containers
- **NGINX (DMZ Server):**
  ```bash
  docker run -d -p 8080:80 --name csf-nginx2 nginx:latest
