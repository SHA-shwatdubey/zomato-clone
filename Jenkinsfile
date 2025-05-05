pipeline {
    agent any
    environment {
        GITHUB_CREDENTIALS = 'github-token'  // Ye wahi credentials ID hai jo aapne Jenkins mein create kiya tha
    }
    stages {
        stage('Checkout') {
            steps {
                // GitHub repository se code ko checkout karna
                git credentialsId: "${GITHUB_CREDENTIALS}", url: 'https://github.com/SHA-shwatdubey/zomato-clone.git'
            }
        }
        stage('Build Backend') {
            steps {
                // Backend ko build karna
                script {
                    // Example build command for the backend
                    sh 'cd backend && npm install && npm run build'
                }
            }
        }
        stage('Build Frontend') {
            steps {
                // Frontend ko build karna
                script {
                    // Example build command for the frontend
                    sh 'cd frontend && npm install && npm run build'
                }
            }
        }
        stage('Run App') {
            steps {
                // App ko run karna
                script {
                    // Example command to start the app
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
