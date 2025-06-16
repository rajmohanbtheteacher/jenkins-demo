<h1 align="center">🚀 CI/CD Pipeline Lab</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Jenkins-CI%2FCD-blue" />
  <img src="https://img.shields.io/badge/Docker-Containerization-blue" />
  <img src="https://img.shields.io/badge/Node.js-App-green" />
</p>

---

## 📦 Project Overview

This is a hands-on lab demonstrating a **production-grade CI/CD pipeline** using:

- 🛠️ **Jenkins** for continuous integration & delivery
- 🐳 **Docker** for containerization
- 🌐 **Node.js** as a sample application
- ☁️ **Docker Hub** as a container registry
- ✅ Optional integrations: SonarQube, GitHub Webhooks

---

## 🧰 Tech Stack

| Tool         | Purpose                      |
|--------------|-------------------------------|
| 🧑‍💻 GitHub     | Source Code Management         |
| ⚙️ Jenkins     | CI/CD Automation              |
| 🐳 Docker      | Build and Run Containers       |
| 📦 Docker Hub  | Image Registry                |
| 🟩 Node.js     | Sample Web Application         |
| 📊 SonarQube   | (Optional) Static Code Analysis|

---

## 🧪 Folder Structure

```bash
ci-cd-lab/
├── app/
│   ├── index.js          # Node.js web server
│   ├── package.json      # Dependencies & scripts
│   └── Dockerfile        # Container build config
├── Jenkinsfile           # CI/CD pipeline
└── README.md             # Project info
```

---

## ⚙️ Pipeline Stages

1. 👨‍💻 Code pushed to GitHub
2. 🧪 Jenkins runs test & build
3. 🔍 SonarQube analyzes quality (optional)
4. 🐳 Docker image built
5. 📤 Image pushed to Docker Hub
6. 🚀 Deployed to staging
7. 🛑 Manual approval
8. 🌍 Deployed to production

---

## 🚀 How to Run the Lab

### 1️⃣ Clone the Repo

```bash
git clone https://github.com/your-org/ci-cd-lab.git
cd ci-cd-lab
```

### 2️⃣ Run Jenkins in Docker

```bash
docker run -d -p 8080:8080 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```

### 3️⃣ Setup Jenkins Pipeline

- Create new pipeline job
- Point to your GitHub repo
- Use included `Jenkinsfile`
- Add DockerHub credentials as `dockerhub-creds`

---

## 🖥️ Accessing the App

```bash
curl http://localhost:3000
```

Expected Output:
```
🚀 Hello from Production Grade CI/CD App!
```

---

## 📷 Screenshots (Optional)
> 💡 Add visuals of your Jenkins pipeline stages or Docker output here.

---

## 👨‍💻 Author

**RajMohan Bharathi**

---

## 📌 Notes

- Secure your credentials using Jenkins Secrets.
- Extend the pipeline with GitHub Webhooks, Slack notifications, or Kubernetes deployments.

---

<p align="center">
  <img src="https://www.jenkins.io/images/logos/jenkins/jenkins.png" width="80" />
  <img src="https://nodejs.org/static/images/logo.svg" width="80" />
  <img src="https://www.docker.com/wp-content/uploads/2022/03/vertical-logo-monochromatic.png" width="80" />
</p>