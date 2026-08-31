pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t aws-devops-backend .'
            }
        }

        stage('Docker Compose') {
            steps {
                sh 'docker compose up -d'
            }
        }

    }
}

