
---

### 📄 `Containers-and-MineMeld.md`

_Source: “NGINX Container” and “MineMeld Deployment” sections_

```markdown
# Containers & MineMeld

Source: NGINX + MineMeld configuration in project documentation.

---

## NGINX Container (DMZ)
- Deployed in DMZ server.  
- Command:
  ```bash
  docker run -d -p 8080:80 --name csf-nginx2 nginx:latest

- Accessible: https://192.168.50.10:8080
- Security policy: internal-inside-dmz (HTTP traffic enabled).
