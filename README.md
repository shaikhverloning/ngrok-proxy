# 🚀 Verloning Local Setup (Docker + Ngrok)

This project runs the full local environment and exposes it publicly using ngrok via Docker.

---

# 📁 Project Structure

Workspace/
├── ngrok-proxy/
   └── nginx.conf
   └── docker-compose.yml
---

# ⚙️ Prerequisites

- Docker Desktop installed  
- Docker Compose available  
- Ngrok account + authtoken  

Get your token:  
https://dashboard.ngrok.com/get-started/your-authtoken

---

# 🔑 Setup Ngrok Token

Replace the token inside `docker-compose.yml`:

NGROK_AUTHTOKEN=YOUR_REAL_TOKEN_HERE

---
# 🌐 Network Setup

docker network ls

If not present:

docker network create verloning-network

---

# ▶️ Run the Project

docker-compose up -d

---

# 🔍 Verify Containers

docker ps

Check ngrok logs:

docker logs -f ngrok-tunnel

---

# 🌍 Get Public URL

You will see:

Forwarding https://xxxx.ngrok-free.app -> http://ngrok-proxy:80

---

# 📱 Use in Flutter App

Update API base URL:

https://xxxx.ngrok-free.app/api

---

# 🧪 Test Locally

curl http://localhost:8081/api/profile

---

# ⚠️ Common Issues

ERR_NGROK_106:
- Wrong or missing authtoken

502 Bad Gateway:
- Backend container not reachable
- Network mismatch
- Wrong service name

docker-compose file not found:
- Run command from correct directory

---

# 🎯 Summary

- Nginx acts as a proxy  
- Ngrok exposes the proxy publicly  
- Docker Compose runs everything together