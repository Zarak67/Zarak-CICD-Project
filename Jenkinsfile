pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking code from GitHub'
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t zarak67/zarak-cicd-project:latest .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    bat 'echo %DOCKER_PASS%| docker login -u %DOCKER_USER% --password-stdin'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                bat 'docker push zarak67/zarak-cicd-project:latest'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deployment stage completed'
            }
        }
    }
}
