pipeline {
    agent any

    stages {
            stage('AWS') {
                agent {
                    docker {
                        image 'amazon/aws-cli'
                        args "--entrypoint=''"
                    }
             }
            steps {
                sh '''
                    aws --version
                '''
             }
            }
            stage('Example') {
                steps {
                    withCredentials([
                        conjurSecretCredential(credentialsId: 'aws-credentials', variable: 'aws-access-key-id')
                    ]) {
                        script {
                            echo "My secret is: ${env.MY_SECRET}"
                        }
                    }
                }
            }
        }
    }