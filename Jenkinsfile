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
                bat 'docker build -t Zarak67/zarak-cicd-project:latest .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                bat 'docker login -u Zarak67 -p zarakbaloch@142657'
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
Testing webhook trigger - CICD pipeline via Jenkins
