pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/SHA-shwatdubey/zomato-clone.git' // Update with your repo URL
        DOCKER_IMAGE_FRONTEND = 'zomato-frontend'
        DOCKER_IMAGE_BACKEND = 'zomato-backend'
    }

    stages {
        stage('Clone Repo') {
            steps {
                // Using credentials to securely clone the repository
                git credentialsId: 'github-token', url: GIT_REPO
            }
        }

        stage('Build Backend') {
            steps {
                // Build backend docker image
                script {
                    dockerImage = docker.build("${DOCKER_IMAGE_BACKEND}", "./backend")
                }
            }
        }

        stage('Build Frontend') {
            steps {
                // Build frontend docker image
                script {
                    dockerImage = docker.build("${DOCKER_IMAGE_FRONTEND}", "./frontend")
                }
            }
        }

        stage('Run App') {
            steps {
                // Run the app using docker-compose (use 'bat' for Windows)
                script {
                    bat 'docker-compose up -d'
                }
            }
        }
    }

    post {
        success {
            echo 'Build and Deployment Successful!'
        }
        failure {
            echo 'Build or Deployment Failed!'
        }
    }
}
