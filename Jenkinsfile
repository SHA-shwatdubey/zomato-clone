pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'your-dockerhub-username/your-image-name'
        DOCKER_TAG = 'latest'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                // e.g., npm run build or mvn package
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // e.g., npm test or mvn test
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
                // e.g., docker run or kubectl apply
            }
        }
    }
}
