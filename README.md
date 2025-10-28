# 🚀 Secure and Scalable Deployment of a Node.js Application on AWS EC2

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/9/93/Amazon_Web_Services_Logo.svg" alt="AWS Logo" width="140"/>
</p>

## Overview
This repository demonstrates deploying a simple **Node.js** application to **AWS EC2 (Ubuntu)** and exposing it to the internet via Security Group rules. It includes a sample server, a sample environment file, and an AWS architecture diagram.

---

## Repo structure (essential)
```
nodejs-aws-deployment/
├── src/
│   └── server.js
├── config/
│   └── sample.env
├── assets/
│   └── aws_architecture_diagram.png
├── .gitignore
├── package.json
├── README.md
└── LICENSE
```

---

## Quick Start (local)
1. Clone the repo and install dependencies:
```bash
git clone <your-repo-url>
cd nodejs-aws-deployment
npm install
```
2. Create a `.env` by copying the sample file:
```bash
cp config/sample.env .env
```
3. Start locally:
```bash
npm start
```
Open `http://localhost:3000` to verify the app is running.

---

## Deploy to AWS EC2 (concise steps)
1. **Create IAM user** (use appropriate permissions or scoped policy). Save credentials securely.
2. **Launch EC2 (Ubuntu)** with a key pair and a security group.
   - Open inbound rule for **HTTP/Custom TCP** (port `3000` or your app port) from your IP or `0.0.0.0/0` (for public access).
   - Allow SSH (port 22) from your trusted IP only.
3. **SSH into the instance**:
```bash
chmod 400 your-key.pem
ssh -i your-key.pem ubuntu@<ec2-public-ip>
```
4. **Install Node.js & Git** and run app on the server:
```bash
sudo apt update
sudo apt install -y nodejs npm git
git clone <your-repo-url>
cd nodejs-aws-deployment
npm install
npm start
```
5. Visit `http://<ec2-public-ip>:3000` (or your chosen port).

---

## sample.env (config/sample.env)
```env
PORT=3000
# Add other environment variables here (do not commit real secrets)
```

---

## .gitignore (created in this repo)
- node_modules/
- .env
- *.log
- .DS_Store

---

