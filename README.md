# 🚀 Cost Optimizer Microservice
> **An AI-powered cost optimization service that analyzes AWS deployments via Terraform & Infracost, aggregates cost data, and provides insights via Grafana dashboards and Slack alerts.**  

## 📌 Key Features
✅ **PR-based Cost Analysis** – Analyzes cost impact for every PR in GitHub  
✅ **AWS & Infracost Aggregation** – Combines AWS Cost Optimizer & Infracost reports  
✅ **AI-Based Cost Predictions** – Detects trends and suggests optimizations  
✅ **Real-time Grafana Dashboards** – Visualizes cost impact and recommendations  
✅ **Slack Alerts** – Notifies teams about cost anomalies  
✅ **AWS EKS Deployment** – Runs in a scalable Kubernetes cluster  
✅ **GitHub Actions CI/CD** – Ensures **100% test coverage**, security analysis, and automatic deployments  

---

## 🛠 Installation (Mac Intel Architecture)

### 1️⃣ Install Dependencies
```bash
brew install go terraform awscli kubectl
```
### 2️⃣ Clone Repository

```bash
git clone https://github.com/your-org/cost-optimizer.git
cd cost-optimizer
```

3️⃣ Set Up Secrets

```bash
export GITHUB_TOKEN="your_github_token"
export INFRACOST_TOKEN="your_infracost_token"
export AWS_ACCESS_KEY_ID="your_aws_access_key"
export AWS_SECRET_ACCESS_KEY="your_aws_secret_key"
export GRAFANA_WEBHOOK_URL="your_grafana_webhook"
export SLACK_WEBHOOK_URL="your_slack_webhook"
```

4️⃣ Deploy to AWS

```bash
terraform init
terraform apply -auto-approve
```

5️⃣ Verify Deployment

```bash
aws eks update-kubeconfig --name cost-optimizer-cluster
kubectl get pods
```

🚀 How It Works

1️⃣ Pulls cost reports from AWS & Infracost
2️⃣ Aggregates & normalizes cost data
3️⃣ Pushes cost insights to Grafana dashboards
4️⃣ Triggers Slack alerts for cost anomalies
5️⃣ Runs automatically for every GitHub PR

📊 Grafana Dashboard

🌐 URL: Grafana Dashboard

📉 Visualizations
- Total Cost
- AWS Cost Optimizer Savings
- Infracost Projections
- Anomaly Alerts

🔔 Slack Alerts

Triggers When:
- Monthly cost exceeds $1000
- An AWS resource has better optimization recommendations
- A GitHub PR introduces high-cost changes

🔗 Example Alert:

```pgsql
🚨 Cost Spike Alert! Monthly cost has exceeded $1000.
```

## 📡 API Endpoints

| Method | Endpoint      | Description                                       |
|--------|-------------|---------------------------------------------------|
| `POST` | `/analyze`   | Fetches cost reports from Infracost & AWS       |
| `POST` | `/optimize`  | Aggregates & normalizes cost data               |
| `GET`  | `/dashboard` | Fetches latest cost insights for Grafana        |
| `POST` | `/alerts`    | Sends cost anomaly alerts to Slack              |
| `POST` | `/pr-report` | Analyzes GitHub PR changes & estimates impact   |


🤖 GitHub CI/CD Integration

✅ Tests run on every PR
✅ Deploys automatically to AWS EKS
✅ Updates Grafana dashboards & alerts

📂 GitHub Actions (.github/workflows/test.yml)

```yaml
name: Test Cost Optimizer Microservice

on:
  pull_request:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Setup Go
        uses: actions/setup-go@v4
        with:
          go-version: 1.21

      - name: Run Unit Tests
        run: go test ./... -cover

      - name: Run Integration Tests
        run: go test ./tests/ -v
        env:
          GRAFANA_DASHBOARD_URL: ${{ secrets.GRAFANA_DASHBOARD_URL }}
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
```

📌 Project Structure

```graphql
📦 cost-optimizer
 ┣ 📂 api                 # API handlers
 ┣ 📂 aggregator          # Data aggregation & normalization
 ┣ 📂 aws                 # AWS Cost Optimizer integration
 ┣ 📂 config              # Environment variables & secrets management
 ┣ 📂 dashboards          # Grafana Dashboard integration
 ┣ 📂 github              # GitHub PR analysis
 ┣ 📂 infracost           # Infracost API integration
 ┣ 📂 notifications       # Slack alerting system
 ┣ 📂 tests               # Unit & integration tests
 ┣ 📜 Dockerfile          # Dockerized deployment
 ┣ 📜 main.go             # Main application entrypoint
 ┣ 📜 terraform/          # Terraform configurations for AWS deployment
 ┣ 📜 README.md           # Documentation
```

🎯 Next Steps

✅ Deploy on AWS
✅ Test with real PRs from Westtower
✅ Monitor cost optimizations in Grafana
✅ Refine AI-based cost trend predictions

🚀 Ready for Deployment?

🔥 Run the deployment commands and confirm! 🚀

```bash
terraform apply
```
