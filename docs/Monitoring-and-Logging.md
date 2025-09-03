
---

### 📄 `Monitoring-and-Logging.md`

_Source: “Syslog Monitoring & Forwarding” section_

# Monitoring & Logging

Source: Syslog + Log forwarding configuration in project documentation.

---

## Syslog Server
- Server IP: **192.168.50.10** (Ubuntu).  
- Syslog Profile created under **Device > Server Profiles > Syslog**.  
- Log Forwarding Profile linked to **all security policies**.  

## Verification
- Real-time monitoring:  
  ```bash
  tail -f /var/log/syslog
  sh /tg/traffic.sh

- Logs exported to CSV via Firewall GUI.
- Successful ping to DMZ server verified connectivity.
