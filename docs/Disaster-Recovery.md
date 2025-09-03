## Proposed DR Design

- HQ firewall connects to **AWS/Azure** via Site-to-Site VPN.  
- DR VMs replicated from on-prem data center to cloud.  
- Automatic failover in case of Calgary HQ outage.  

---

## Benefits
- Ensures resilience against local disasters (e.g., floods).  
- Cloud-hosted replicas minimize downtime.  
- Hybrid model integrates on-prem + cloud security.  
