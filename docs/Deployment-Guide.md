# Deployment Guide

This guide outlines how the Palo Alto Firewall v10.0 lab pod was deployed using VMware Workstation.  
Source: Lab Solution instructions in project documentation.

---

## VMware Workstation Setup

1. Open **Virtual Network Editor** (Edit > Virtual Network Editor).  
2. Configure **VMnets** for the lab:
   - VMnet0 → Bridged (connect to host)
   - VMnet8 → NAT (DHCP enabled)
   - VMnet1 → Host-only → 192.168.1.0/24
   - VMnet2 → 203.0.113.0/24
   - VMnet3 → 192.168.50.0/24
   - VMnet4 → 0.0.0.0/24
   - VMnet5 → 1.1.1.0/24

3. Ensure VMnet8 NAT subnet is unique (not overlapping 192.168.1.0/24).  

---

## Import VMs

### Firewall (VM-50)
- Import `PA-VM-10.0-PanOSFirewall.ova`  
- Assign NICs to VMnets 1–5, plus host-only.  
- Set MAC addresses (example: 00:50:56:8A:7C:78 for NIC1).  
- Allocate at least **5.5 GB RAM**.  

### Virtual Router
- Import `PA-VM-10.0-PanOS-VRouter.ova`  
- NICs:
  - Adapter1: NAT (VMnet8)
  - Adapter2: VMnet1
  - Adapter3: VMnet2
- Confirm IPs using `ifconfig`.

### DMZ Server
- Import `PA-VM-10.0-PanOS-DMZ.ova`  
- NICs:
  - Adapter1: VMnet3
  - Adapter2: VMnet4
- Login: `root / Pal0Alt0!`

### Client
- Import `PA-VM-10.0-PanOS-Client.ova`  
- NIC1: VMnet1  
- Login: `lab-user / Pal0Alt0!`

---

## Licensing Firewall

1. Boot the **VM-50 Firewall**.  
2. Ensure Virtual Router is running (Internet access).  
3. Login: `admin / Pal0Alt0!`  
4. Verify IP:  
   ```bash
   show interface management
   ping host 8.8.8.8

5. Connect via WebUI: https://192.168.1.254
6. Load base.xml config snapshot.
7. Commit changes.
8. Navigate to Device > Licenses → Activate using authorization code.
9. Firewall reboots, licenses applied.
10. Update Apps & Threats + Antivirus (Device > Dynamic Updates).
