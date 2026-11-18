pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t bca-cicd-demo:latest .'
            }
        }

        stage('Deploy Application') {
            steps {
                sh 'docker rm -f bca-cicd-demo || true'
                sh 'docker run -d --name bca-cicd-demo -p 8081:80 bca-cicd-demo:latest'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'docker ps --filter name=bca-cicd-demo'
            }
        }
    }
}