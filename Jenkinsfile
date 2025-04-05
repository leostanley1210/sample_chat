pipeline {
    agent any
    tools {
    git 'Default'
    jdk 'jdk17'
    }
     stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'ssh-connection', url: 'git@github.com:leostanley1210/Chat_Room.git', branch: 'master'
            }
        }

        stage('compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
