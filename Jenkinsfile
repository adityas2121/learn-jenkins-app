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
                        conjurSecretCredential(credentialsId: 'aws-credentials/aws-access-key-id', variable: 'MY_SECRET')
                    ]) {
                        script {
                            echo "My secret is: $\$MY_SECRET"
                        }
                    }
                }
            }
        }
    }