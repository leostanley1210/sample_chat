pipeline {
    agent any
    tools {
        maven 'maven'
    }

    stages {
        stage('GIT SCM') {
            steps{
                git credentialsId: 'ssh', url: 'git@github.com:leostanley1210/sample_chat.git'
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
