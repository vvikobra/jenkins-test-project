pipeline {
    agent any
    stages {
        stage('Install Go') {
            steps {
                sh '''
                    if [ ! -f /usr/local/go/bin/go ]; then
                        echo "Installing Go 1.22.5..."
                        cd /tmp
                        curl -LO https://go.dev/dl/go1.22.5.linux-amd64.tar.gz
                        tar -C /usr/local -xzf go1.22.5.linux-amd64.tar.gz
                    fi
                '''
            }
        }
        stage('Unit Tests') {
            steps {
                sh 'PATH=/usr/local/go/bin:$PATH go test -v -run="TestHandler|TestHandler2"'
            }
        }
        stage('Integration Test') {
            steps {
                sh 'PATH=/usr/local/go/bin:$PATH go test -v -run="TestIntegration"'
            }
        }
    }
}