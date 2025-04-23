# Setup Steps for Docker Compose on AWS EC2

```bash
# SSH into EC2 and create working directory
mkdir compose && cd compose

# Download Docker Compose file
wget https://raw.githubusercontent.com/devopshydclub/vprofile-project/docker/compose/docker-compose.yml

# Launch services
docker compose up -d

# Check status
docker compose ps
```

🧭 Visit `http://<EC2_PUBLIC_IP>` in browser.
