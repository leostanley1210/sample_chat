pipeline {
  agent any

  environment {
    IMAGE_NAME = 'your-dockerhub-username/chat-app:latest'
  }

  stages {
    stage('Clone Repo') {
      steps {
        git 'https://github.com/leostanley1210/sample_chat.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t $IMAGE_NAME .'
      }
    }

    stage('Push to DockerHub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-password', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
          sh 'echo $PASS | docker login -u $USER --password-stdin'
          sh 'docker push $IMAGE_NAME'
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
