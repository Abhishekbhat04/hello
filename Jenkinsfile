pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker-hub-creds') // Replace with your Docker Hub credentials ID
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Abhishekbhat04/DevOps1.git', credentialsId: 'github-creds'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("abhishekbhat04/my-web-app")
                }
            }
        }

        stage('Push Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKERHUB_CREDENTIALS) {
                        dockerImage.push("latest")
                    }
                }
            }
        }
    }
}
