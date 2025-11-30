pipeline {
    agent {
        docker {
            image 'golang:1.22-alpine'
            args '-u root'  
        }
    }

    stages {
        stage('Unit Tests') {
            steps {
                sh 'go test -v -run="TestHandler|TestHandler2"'
            }
        }
        stage('Integration Test') {
            steps {
                sh 'go test -v -run="TestIntegration"'
            }
        }
    }
}