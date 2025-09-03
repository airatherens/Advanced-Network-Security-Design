# Security Policies

Source: Security configurations section of project documentation.

---

## Data Filtering
- Profile created: Detects **SSNs** (regex pattern match).  
- Applied to policy: **Allow-Inside-External**.  
- Action: **Alert**.  

## File Blocking
- Profile: Blocks **PDF files** (upload & download).  
- Applied to security policy.  
- Custom `block-list.txt` denies access to listed domains.  

## International Geo-Blocking
- Policy: **Block International**.  
- Source countries: **Cuba, Bahamas, Chad**.  
- Action: **Deny**.  

## Reconnaissance Protection
- Zone Protection Profiles applied to **External** + **DMZ**.  
- Enabled: Flood protection, Reconnaissance protection.  
- Verified logs:  
  ```bash
  sh /tg/traffic.sh
  sudo tail -f /var/log/syslog
