# **GitHub Actions - Complete Notes for DevOps Engineers** 🚀  

## **1️⃣ What is GitHub Actions?**  
GitHub Actions is a **CI/CD (Continuous Integration/Continuous Deployment) tool** built into GitHub that allows you to automate workflows like:  
✅ **Building** and **testing** code  
✅ **Deploying** applications  
✅ **Running security scans**  
✅ **Automating DevOps tasks**  

It runs workflows **inside GitHub repositories** using YAML configuration files stored in `.github/workflows/`.  

---

## **2️⃣ Key Concepts in GitHub Actions**
| **Concept** | **Description** |
|------------|----------------|
| **Workflows** | Define automation processes (CI/CD pipelines). Stored in `.github/workflows/`. |
| **Events (`on:`)** | Triggers that start the workflow (e.g., `push`, `pull_request`, `schedule`). |
| **Jobs** | A sequence of steps executed in a runner (e.g., `build`, `test`, `deploy`). |
| **Steps** | Individual commands executed inside a job (e.g., `run: npm install`). |
| **Actions (`uses:`)** | Reusable components that perform common tasks (e.g., `actions/checkout@v3`). |
| **Runners** | Machines that execute jobs (GitHub-hosted or self-hosted). |
| **Secrets (`secrets.GITHUB_TOKEN`)** | Secure storage for sensitive data like API keys and credentials. |

---

## **3️⃣ GitHub-Hosted vs. Self-Hosted Runners**
| Feature | GitHub-Hosted Runners | Self-Hosted Runners |
|---------|----------------------|----------------------|
| **Setup** | No setup required | Manual setup needed |
| **Customization** | Limited | Full control over environment |
| **Cost** | Free (limited for private repos) | You pay for your own hardware |
| **Security** | Managed by GitHub | You manage security |
| **Use Case** | Small to medium projects | Large-scale, enterprise workloads |

---

## **4️⃣ Writing a Basic GitHub Actions Pipeline**
📌 **Create a file:** `.github/workflows/ci-pipeline.yml`  
```yaml
name: CI/CD Pipeline  # Workflow name

on: 
  push:
    branches: [ main ]  # Runs on push to 'main' branch

jobs:
  build:
    runs-on: ubuntu-latest  # Use GitHub-hosted runner
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3

      - name: Install Dependencies
        run: npm install

      - name: Run Tests
        run: npm test

      - name: Build Project
        run: npm run build
```

---

## **5️⃣ Common Events (`on:`)**
| **Event** | **Description** |
|----------|----------------|
| `push` | Runs workflow on `git push` |
| `pull_request` | Runs workflow when a PR is created or updated |
| `schedule` | Runs workflow on a schedule (cron job) |
| `workflow_dispatch` | Manually trigger workflow |

Example: **Scheduled Job (Daily at Midnight)**
```yaml
on:
  schedule:
    - cron: "0 0 * * *"  # Runs at 12 AM UTC daily
```

---

## **6️⃣ Jobs & Dependencies (`needs:`)**
- Jobs run **in parallel** by default.  
- Use `needs:` to run jobs **sequentially**.  

Example: **Build → Test → Deploy (Sequential Execution)**  
```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: echo "Building app"

  test:
    needs: build  # Runs after 'build' job
    runs-on: ubuntu-latest
    steps:
      - run: echo "Running tests"

  deploy:
    needs: test  # Runs after 'test' job
    runs-on: ubuntu-latest
    steps:
      - run: echo "Deploying app"
```

---

## **7️⃣ Using Secrets & Environment Variables**
- **Secrets:** Stored securely in GitHub (`Settings → Secrets → Actions`).  
- **Environment Variables:** Set within workflows or jobs.  

Example: **Using Secrets in a Workflow**
```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to AWS
        run: aws s3 sync ./build s3://my-bucket
        env:
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```

---

## **8️⃣ Matrix Builds (Run on Multiple Environments)**
Used for testing across multiple OS or Node.js versions.  

Example: **Run Tests on Multiple Node.js Versions**
```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [14, 16, 18]  # Run on 3 Node.js versions
    steps:
      - uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node-version }}
      - run: npm install && npm test
```

---

## **9️⃣ Caching Dependencies**
Speed up workflows by caching dependencies.  

Example: **Cache Node.js Dependencies**
```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/cache@v3
        with:
          path: ~/.npm  # Cache location
          key: node-modules-${{ hashFiles('package-lock.json') }}
```

---

## **🔟 Deployment Examples**
### **1️⃣ Deploy to AWS S3**
```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to S3
        run: aws s3 sync ./build s3://my-bucket --delete
```

### **2️⃣ Deploy to Kubernetes (K8s)**
```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Set up kubectl
        run: |
          curl -LO "https://dl.k8s.io/release/v1.21.0/bin/linux/amd64/kubectl"
          chmod +x kubectl && mv kubectl /usr/local/bin/
      - name: Deploy to Kubernetes
        run: kubectl apply -f deployment.yaml
```

---

## **🔢 GitHub Actions vs. Jenkins vs. GitLab CI**
| Feature | GitHub Actions | Jenkins | GitLab CI |
|---------|---------------|---------|-----------|
| **Setup** | Easy | Complex | Moderate |
| **Hosted Runners** | Yes | No (requires setup) | Yes |
| **Customization** | Moderate | High | High |
| **Scalability** | Auto-scaled | Manual | Auto-scaled |
| **Best for** | GitHub projects | Enterprises | GitLab users |

---

## **🔥 Best Practices for GitHub Actions**
✅ **Use specific action versions** (e.g., `uses: actions/checkout@v3`)  
✅ **Avoid hardcoding secrets** – Use **GitHub Secrets**  
✅ **Use caching** for dependencies to improve speed  
✅ **Limit permissions** (use `GITHUB_TOKEN` with least privilege)  
✅ **Use matrix builds** for testing multiple environments  
✅ **Use workflows for automation** – CI/CD, security checks, infrastructure as code (IaC)  

---

## **🎯 Final Thoughts**
✅ **GitHub Actions is a powerful and flexible CI/CD tool**  
✅ **Best suited for GitHub-based projects**  
✅ **Automates software development workflows seamlessly**  
✅ **Can be integrated with AWS, Kubernetes, Terraform, and more**  

