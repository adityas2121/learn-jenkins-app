pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            stage('AWS')
            agent {
                docker {
                    image 'amazon/aws-cli'
                }
            }
            steps {
                sh '''
                    aws --version
                '''
            }
        }
    }
}

            /*
            steps {
                sh '''
                ls -la
                node --version
                npm --version
                npm ci
                npm run build
                ls -la
                '''
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                echo 'Test Stage'
                sh '''
                    test -f build/index.html'
                    npm test
                    '''
            }
        }
    }
}
