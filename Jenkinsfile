pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'your-dockerhub-username/zomato-clone'
        DOCKER_TAG = 'latest'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/SHA-shwatdubey/zomato-clone.git'
            }
        }

        stage('Frontend Docker Build & Push') {
            steps {
                script {
                    // Frontend Docker image build
                    docker.build("${DOCKER_IMAGE}-frontend:${DOCKER_TAG}", './frontend')
                    
                    // Push to Docker Hub
                    docker.withRegistry('', 'docker-hub-credentials-id') {
                        docker.image("${DOCKER_IMAGE}-frontend:${DOCKER_TAG}").push()
                    }
                }
            }
        }

        stage('Backend Docker Build & Push') {
            steps {
                script {
                    // Backend Docker image build
                    docker.build("${DOCKER_IMAGE}-backend:${DOCKER_TAG}", './backend')
                    
                    // Push to Docker Hub
                    docker.withRegistry('', 'docker-hub-credentials-id') {
                        docker.image("${DOCKER_IMAGE}-backend:${DOCKER_TAG}").push()
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // e.g., docker run or kubectl apply
            }
        }
    }
}

