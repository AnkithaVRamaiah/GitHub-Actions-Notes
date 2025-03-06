# GitHub-Actions-Notes

## **🔹 Topics to Learn in GitHub Actions for DevOps Engineers**  

### **1️⃣ Basics of GitHub Actions**  
✅ What is GitHub Actions?  
✅ Benefits of GitHub Actions (CI/CD, automation, workflows)  
✅ GitHub Actions vs. Jenkins vs. GitLab CI  

---

### **2️⃣ Core Concepts**  
✅ **Workflows** – Structure, `.github/workflows/` directory  
✅ **Events (`on:`)** – Triggers (push, pull_request, schedule, manual trigger)  
✅ **Jobs** – Running steps in parallel/sequentially  
✅ **Steps** – Individual actions inside a job  
✅ **Actions (`uses:`)** – Reusable components  
✅ **Runners** – GitHub-hosted vs. self-hosted runners  
✅ **Secrets & Environment Variables**  

---

### **3️⃣ Writing GitHub Workflows (YAML)**  
✅ Creating a `.yml` file for GitHub Actions  
✅ Running jobs on different OS (Ubuntu, Windows, macOS)  
✅ Running multiple commands in steps (`run:`)  
✅ Using official and custom **actions** (`uses: actions/checkout@v3`)  
✅ Using **conditionals** (`if:`) for controlling execution  
✅ Handling **job dependencies** (`needs:`)  

---

### **4️⃣ Advanced GitHub Actions Concepts**  
✅ **Matrix Builds** – Running tests on multiple OS/versions  
✅ **Caching Dependencies** – Speed up builds (`actions/cache@v3`)  
✅ **Artifacts & Uploading Files** – Storing logs, build files (`actions/upload-artifact@v3`)  
✅ **Parallel & Sequential Jobs** – Controlling execution order  
✅ **Notifications & Alerts** – Slack, email integration  

---

### **5️⃣ Secrets & Security Best Practices**  
✅ Storing **secrets** in GitHub (`secrets.GITHUB_TOKEN`)  
✅ Using **encrypted secrets** instead of hardcoding credentials  
✅ Restricting **permissions** (e.g., least privilege for `GITHUB_TOKEN`)  

---

### **6️⃣ Automating Workflows with GitHub Actions**  
✅ **CI/CD Pipeline** – Build, test, deploy  
✅ **Running Scheduled Jobs** (`cron` expressions)  
✅ **Triggering Workflows Manually** (`workflow_dispatch`)  
✅ **Linting & Code Quality Checks** (ESLint, Pylint, SonarQube)  
✅ **Security Scanning** (Trivy, Snyk, Dependabot)  

---

### **7️⃣ Deployment with GitHub Actions**  
✅ Deploying to **AWS (S3, EC2, Lambda, EKS)**  
✅ Deploying to **Kubernetes (kubectl, Helm)**  
✅ Deploying to **Docker Hub & GitHub Container Registry**  
✅ Deploying to **Terraform (Infrastructure as Code - IaC)**  
✅ Deploying to **Azure & GCP**  

---

### **8️⃣ Monitoring & Debugging**  
✅ Viewing workflow **logs** and debugging failures  
✅ Using **set -x** for debugging shell scripts  
✅ **Re-running failed jobs** manually  
✅ **Retry Strategies** for flaky tests or network issues  

---

### **9️⃣ Integrating GitHub Actions with Other DevOps Tools**  
✅ GitHub Actions + **Jenkins** (hybrid CI/CD setup)  
✅ GitHub Actions + **ArgoCD** (GitOps Deployment)  
✅ GitHub Actions + **Terraform** (Infrastructure automation)  
✅ GitHub Actions + **Slack/MS Teams** (notifications)  

---

### **🔟 Best Practices for GitHub Actions**  
✅ Use **specific action versions** (`@v3` instead of `@latest`)  
✅ Avoid **hardcoded secrets**, always use **GitHub Secrets**  
✅ Use **caching** to speed up builds  
✅ Minimize permissions for **security**  
✅ Use **modular workflows** and reusable actions  

---

## **🎯 Where to Go from Here?**  
📌 Start with **simple workflows** → Move to **complex CI/CD pipelines**  
📌 Experiment with **deploying apps** (AWS, Kubernetes)  
📌 Learn about **GitHub Actions Marketplace** for pre-built actions  

