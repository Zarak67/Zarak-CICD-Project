pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking code from GitHub'
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t Zarak67/zarak-cicd-project:latest .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                bat 'echo %DOCKERHUB_CREDENTIALS_PSW% | docker login -u %DOCKERHUB_CREDENTIALS_USR% --password-stdin'
            }
        }
        stage('Push Docker Image') {
            steps {
                bat 'docker push Zarak67/zarak-cicd-project:latest'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deployment stage completed'
            }
        }
    }
}
