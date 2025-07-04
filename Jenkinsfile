pipeline {
  agent any

  environment {
    IMAGE_NAME = 'leostanely1210/chat-app:latest'
  }

  stages {
    stage('Clone Repo') {
      steps {
        git 'https://github.com/leostanley1210/sample_chat.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t leostanley1210/chat-app:latest .'
      }
    }

   stage('Push to DockerHub') {
    steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
            sh '''
              echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
              docker push leostanley1210/chat-app:latest
            '''
        }
    }
}
    stage('Deploy to Kubernetes') {
      steps {
        sh 'kubectl apply -f kubernetes/'
      }
    }
  }
}
