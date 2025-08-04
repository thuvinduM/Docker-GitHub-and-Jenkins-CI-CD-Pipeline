# Docker, GitHub & Jenkins CI/CD Pipeline

This repository demonstrates a complete CI/CD pipeline using Jenkins, Docker, and GitHub. It automates the steps of pulling code from GitHub, building a Docker image, logging into Docker Hub, and pushing the image to your Docker Hub repository using a declarative Jenkinsfile.

## Technologies Used

- Jenkins
- Docker
- GitHub
- Node.js (as the sample application)

## Pipeline Overview

The Jenkins pipeline defined in the `Jenkinsfile` consists of the following stages:

1. **SCM Checkout**: Pulls the latest code from the `main` branch of the connected GitHub repository.
2. **Build Docker Image**: Uses the Dockerfile in the repo to build a Docker image and tags it using the Jenkins environment variable `BUILD_NUMBER`.
3. **Login to Docker Hub**: Logs into Docker Hub using credentials stored securely in Jenkins Credentials Manager.
4. **Push Image**: Pushes the built Docker image to your Docker Hub repository.
5. **Post Actions**: Logs out from Docker Hub.

## Prerequisites

- Jenkins installed and running on your machine
- Docker installed and running on the Jenkins host
- A Docker Hub account and an access token/password stored in Jenkins Credentials Manager
- A GitHub repository connected to Jenkins

## Credentials Setup

In Jenkins, go to **Manage Jenkins > Credentials**, and add the following:
- **Kind**: Secret Text
- **ID**: `test-dockerpass`
- **Secret**: Your Docker Hub access token or password

## Sample Jenkinsfile Logic

The `Jenkinsfile` uses Windows-style batch (`bat`) commands and the `env.BUILD_NUMBER` variable to dynamically tag Docker images.

## Docker Image Format

The Docker image is built and pushed with the tag:  
`adomicarts/nodeapp-cuban:<BUILD_NUMBER>`

## How to Use

1. Clone this repository or fork it to your GitHub.
2. Set up a Jenkins job and point it to this repo.
3. Configure Docker and Jenkins credentials as described above.
4. Run the pipeline. Jenkins will pull code, build the image, log in to Docker Hub, and push the image automatically.

## Author

Thuvindu Muthukumara

