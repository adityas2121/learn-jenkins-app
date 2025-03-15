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
            stage('AWS') {
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
}