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
            stage('Conjur') {
                steps {
                    withCredentials([
                        conjurSecretCredential(credentialsId: 'aws-credentials', variable: 'aws-access-key-id')
                    ]) {
                        script {
                            echo "My secret is: ${env.aws-access-key-id}"
                        }
                    }
                }
            }
        }
    }