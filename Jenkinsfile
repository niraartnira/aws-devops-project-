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

        stage('Run Tests') {
            steps {
                sh 'docker run --rm aws-devops-backend python -c "import app; print(\"Application test successful\")"'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker stop aws-devops-backend || true'
                sh 'docker rm aws-devops-backend || true'
                sh 'docker run -d --name aws-devops-backend -p 5000:5000 aws-devops-backend'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully.'
        }

        failure {
            echo 'CI/CD Pipeline failed.'
        }
    }
}
