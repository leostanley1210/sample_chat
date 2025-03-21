pipeline {
    agent any
    tools {
        maven 'maven'
    }

    stages {
        stage('GIT SCM') {
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
