pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3001:3000'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm intsall webpack -dev-server -g'
            }
        }
    }
}
