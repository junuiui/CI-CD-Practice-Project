# CI/CD Fundamentals

## CI (Continuous Integration)

> The process of automatically verifying code quality and integrity when developers merge their code into a shared repository (GitHub, GitLab, etc.).

- **Build**
  - Converting the written code into an executable format (Compile, Build, etc.).
- **Test**
  - Automatically checking if the new code breaks existing features or contains errors.
- **Objective**
  - To detect code conflicts early and maintain a "deployable state" at all times.

---

## CD (Continuous Delivery/Deployment)

> The process of delivering clean, CI-verified code to actual users.

- **Continuous Delivery**
  - The code is ready to be deployed, but the final deployment requires human approval (a "manual trigger").
- **Continuous Deployment**
  - The code is automatically reflected in the production server once it passes all tests without any human intervention.
- **Objective**
  - To eliminate the manual labor of developers logging into servers and uploading files.

---

## CI/CD Workflow (Pipeline)

> All these processes are connected like a single pipeline.

- **Code**
  - A developer executes a `git push` with their code changes.
- **Build**
  - A CI server (e.g., GitHub Actions) fetches the code and builds it.
- **Test**
  - Automated test scripts run. (The process stops here if an error occurs).
- **Release/Deploy**
  - Once tests pass, it creates a Docker image or transfers files to the server (AWS EC2/S3, etc.).