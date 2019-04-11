pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3001:3000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm intsall webpack -dev-server -g'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'finished using the web site? (click "proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
