pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'your-dockerhub-username/zomato-clone'
        DOCKER_TAG = 'latest'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git credentialsId: 'github-token', url: 'https://github.com/SHA-shwatdubey/zomato-clone.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                // Example: npm install && npm run build
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Example: npm test
            }
        }

        stage('Docker Build & Push') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}:${DOCKER_TAG}")
                    docker.withRegistry('', 'docker-hub-credentials-id') {
                        docker.image("${DOCKER_IMAGE}:${DOCKER_TAG}").push()
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Example: docker run -d -p 3000:3000 your-dockerhub-username/zomato-clone:latest
            }
        }
    }
}
