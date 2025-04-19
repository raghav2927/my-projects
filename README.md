# 🚀 Medicure CI/CD with GenAI Integration

This project demonstrates a complete CI/CD pipeline using Jenkins and Docker for the [Medicure Spring Boot App](https://github.com/StarAgileDevOpsTraining/star-agile-health-care.git), with AI-enhanced features via OpenAI GPT-4.

---

## 🔧 Tech Stack

- **Spring Boot** - Medicure Microservice App
- **Jenkins** - CI/CD automation
- **Docker** - Build and deployment
- **OpenAI GPT-4** - Commit analysis and release notes
- **Prometheus + Grafana** *(optional)* - Monitoring

---

## 🛠️ Setup Instructions

### 1. Prerequisites

- Jenkins installed and running
- Docker installed (on the same machine as Jenkins)
- GitHub account (for source code)
- DockerHub account (for image registry)
- OpenAI API Key

---

### 2. Jenkins Setup

- Create a **Pipeline Job**
- Add the following **credentials** in Jenkins:
  - `docker-hub-creds`: Username + Password (for DockerHub)
  - `openai-api-key`: Secret text (for OpenAI GPT API)

---

### 3. Jenkinsfile Pipeline Steps

- Clone source code
- Build the Spring Boot JAR
- Generate AI-powered release notes from Git commits
- Build Docker image and push to DockerHub
- Run the latest container on port `8081`

---

## 🤖 GenAI Integration (GPT-4)

> The power of GPT-4 is used to enhance DevOps automation:

### ✅ Commit-Based Release Notes
- Recent Git commits are analyzed
- A prompt is sent to GPT-4 to create release notes
- Results are printed in Jenkins console

---

## 📊 Monitoring Setup (Optional)

You can use Prometheus + Grafana for container monitoring:

```bash
git clone https://github.com/prometheus/prometheus
cd prometheus
docker-compose up -d
```

---

## 🚀 How to Run

- Start Jenkins and Docker
- Trigger the pipeline from Jenkins
- View the output:
  - AI-generated release notes
  - Docker image pushed to DockerHub
  - Container running at `http://localhost:8081`

---

## 🧠 Extend GenAI Usage (Ideas)

- Auto classify build failures (infra, code, test)
- Generate Slack alerts with summaries
- AI-based test coverage analysis
- Real release notes from Git diff