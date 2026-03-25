# 🚀 Static Website Deployment to AWS S3 using GitHub Actions

This project demonstrates how to automatically deploy a static website to AWS S3 using GitHub Actions (CI/CD).

---

## 📂 Project Overview

This repository contains a simple static website built with:

* HTML
* CSS
* JavaScript

Changes pushed to the `main` branch are automatically deployed to an S3 bucket.

---

## ⚡ CI/CD Workflow

GitHub Actions is used to automate deployment.

### 🔁 Workflow Steps

1. Checkout repository
2. Configure AWS credentials securely
3. Sync project files to S3

---

## 📄 GitHub Actions Workflow

Location:

```bash
.github/workflows/main.yml
```

### 🧾 Workflow Configuration

```yaml
name: Deploy to S3

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Configure AWS Credentials
        uses: aws-actions/configure-aws-credentials@v4
        with:
          aws-access-key-id: \${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: \${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: <your-region>

      - name: Upload files to S3 bucket
        run: |
          aws s3 sync . s3://<your-bucket-name> --delete
```

> Replace `<your-region>` and `<your-bucket-name>` with your own values.

---

## 🔐 Security Best Practices

* Do **not** hardcode AWS credentials
* Use GitHub Secrets:

  * `AWS_ACCESS_KEY_ID`
  * `AWS_SECRET_ACCESS_KEY`
* Avoid exposing bucket names or infrastructure details publicly
* Follow least-privilege IAM policies

---

## ☁️ AWS S3 Setup

1. Create an S3 bucket
2. Enable **Static Website Hosting**
3. Configure:

   * Index document → `index.html`
4. Set appropriate bucket permissions

---

## 🌐 Deployment Flow

* Push code to `main`
* GitHub Actions runs automatically
* Files are synced to S3
* Website updates instantly

---

## 📁 Project Structure

```
.
├── index.html
├── commitee1.html
├── script.js
├── styles.css
└── .github/workflows/main.yml
```

---

## 🛠 Tech Stack

* HTML, CSS, JavaScript
* AWS S3
* GitHub Actions

---

## 🎯 Purpose

This project demonstrates:

* CI/CD pipeline automation
* Secure cloud deployment practices
* Static website hosting on AWS

---

## 📄 License

MIT License
