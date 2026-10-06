# Task 2: Jenkins Pipeline for CI/CD

## Objective
Automate build, test and deploy of a Node.js app using a Jenkins pipeline.

## Tools
Jenkins (running in Docker), Docker, GitHub, Node.js

## Pipeline stages (Jenkinsfile)
1. **Build**: builds the Docker image
2. **Test**: runs the image and verifies the app loads
3. **Deploy**: removes old container and runs the new one on port 3001

## Trigger
Poll SCM (`* * * * *`): Jenkins checks the repo every minute and builds on new commits.

## How to run
1. Start Jenkins: `docker run -d --name jenkins -p 8081:8080 -v jenkins_home:/var/jenkins_home -v //var/run/docker.sock:/var/run/docker.sock --user root jenkins/jenkins:lts-jdk17`
2. Create a Pipeline job using "Pipeline script from SCM" pointing to this repo.
3. Click Build Now, then open http://localhost:3001

## Files
- `Jenkinsfile`: pipeline definition
- `Dockerfile`, `app.js`, `server.js`, `test/`: sample app
- `screenshots/`: Jenkins dashboard and app screenshots
