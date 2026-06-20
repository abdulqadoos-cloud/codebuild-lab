# AWS CodeBuild Container Pipeline Lab

A secure, fully dynamic CI/CD automated pipeline built with **AWS CodeBuild** and **Amazon ECR** to containerize and publish a Node.js web application. 

This repository demonstrates modern DevOps best practices, featuring dynamic image tagging strategies designed to comply with ECR tag immutability constraints.

---

## 🏗️ Architecture Flow



1. **Source:** Developer pushes code changes to the `master` branch on GitHub.
2. **Build:** AWS CodeBuild triggers on-demand, fetches the source code, and initiates the environment.
3. **Authentication:** CodeBuild securely requests an authorization token via the AWS CLI and logs into the private Amazon ECR registry.
4. **Compile & Build:** CodeBuild execution pulls the base image securely from the AWS ECR Public Gallery and builds the local Docker image layers.
5. **Tag & Push:** The built image is uniquely tagged utilizing an integrated Git commit hash and AWS build-number sequence before being pushed to the ECR repository.

---

## 🛠️ Repository Structure

```text
codebuild-lab/
├── Dockerfile          # Multi-layer container build definitions
├── app.js              # Application entry point
├── package.json        # Node.js dependencies
└── buildspec.yml       # AWS CodeBuild phases configuration