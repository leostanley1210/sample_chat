pipeline {
    agent {lable 'slave'}
    tools {
        maven 'maven'
    }

    stages {
        stage('checkout') {
            steps {
                git 'https://github.com/leostanley1210/Chat_Room.git'
            }
        }
    
        stage ('compile') {
            steps {
                sh 'mvn compile'
            }
        }
           
        stage ('build') {
            steps {
                 sh 'mvn package'
           }
         }
    }

}         
