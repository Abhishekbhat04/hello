pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/your-username/your-repo.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          dockerImage = docker.build("my-web-app:${env.BUILD_ID}")
        }
      }
    }

    stage('Push Image') {
      steps {
        withDockerRegistry([credentialsId: 'docker-hub-creds', url: '']) {
          script {
            dockerImage.push()
          }
        }
      }
    }
  }
}
