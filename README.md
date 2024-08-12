# SIT753_5.1
pipeline {
    agent any
    environment {
        DIRECTORY_PATH = '/home/jenkinw'
        TESTING_ENVIRONMENT = 'TestEnv'
        PRODUCTION_ENVIRONMENT = 'Muhammad_Zain_UL_Abidin'
    }
    stages {
        stage('Build') {
            steps {
                echo "fetch the source code from the directory path specified by the environment variable: ${env.DIRECTORY_PATH}"
                echo 'compile the code and generate any necessary artifacts'
            }
        }
        stage('Test') {
            steps {
                echo 'unit tests'
                echo 'integration tests'
            }
        }
        stage('Code Quality Check') {
            steps {
                echo 'check the quality of the code'
            }
        }
        stage('Deploy') {
            steps {
                echo "deploy the application to a testing environment specified by the environment variable: ${env.TESTING_ENVIRONMENT}"
            }
        }
        stage('Approval') {
            steps {
                script {
                    echo 'Waiting for manual approval...'
                    sleep 10
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "deploy the code to the production environment using the environment variable specifying the environment name: ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}
