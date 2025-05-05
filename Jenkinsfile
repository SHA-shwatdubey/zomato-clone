pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/your-username/zomato-clone.git'
            }
        }

        stage('Build Backend') {
            steps {
                sh 'docker build -t zomato-backend ./backend'
            }
        }

        stage('Build Frontend') {
            steps {
                sh 'docker build -t zomato-frontend ./frontend'
            }
        }

        stage('Run App') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
