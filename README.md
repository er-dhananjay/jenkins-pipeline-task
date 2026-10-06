# Node.js Demo App: CI/CD with GitHub Actions

## Objective
Automate test, build and deploy of a Node.js web app using GitHub Actions and Docker Hub.

## Tools
GitHub, GitHub Actions, Node.js, Express, Docker, Docker Hub

## Pipeline flow
Triggered on every push to `main`:
1. **test** job: checkout, setup Node.js 20, `npm install`, `npm test`
2. **build-and-push** job (runs only if tests pass): login to Docker Hub using secrets, build the Docker image, push it as `nodejs-demo-app:latest`

## Files
- `app.js`, `server.js`: Express app
- `test/app.test.js`: test using Node's built-in test runner
- `Dockerfile`: container image definition
- `.github/workflows/main.yml`: CI/CD workflow
- `screenshots/`: pipeline and Docker Hub screenshots

## Secrets used
`DOCKERHUB_USERNAME`, `DOCKERHUB_TOKEN` (stored in GitHub Actions secrets, not in code)
