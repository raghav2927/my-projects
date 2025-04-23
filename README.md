# VProfile Project – DevOps Deployment Showcase

This repo contains full DevOps deployment scenarios for the VProfile Spring Boot application.

---

## 📦 Deployments Included

### 🖥️ Local Machine (Vagrant)
| Method     | Description                            |
|------------|----------------------------------------|
| Manual     | Full step-by-step provisioning         |
| Automated  | Provisioning via Vagrant + Shell scripts |

### ☁️ AWS EC2 (Docker Compose)
Run all VProfile components in containers using `docker-compose` on Ubuntu EC2 instance.

---

## 🛠️ Tech Stack
- Vagrant + VirtualBox
- MySQL, Memcache, RabbitMQ, Tomcat, Nginx
- Docker, Docker Compose
- AWS EC2 (Ubuntu)

---

## 📁 Folder Overview

```
local-setup/
│
├── manual/        # Manual Vagrant provisioning
└── automated/     # Automated Vagrant + Scripts

aws-deployment/
└── docker-compose/ # Dockerized setup on EC2
```
