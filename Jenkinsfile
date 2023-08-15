pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "DIRECTORY_PATH"
        TESTING_ENVIRONMENT = "TESTING_ENVIRONMENT"
        PRODUCTION_ENVIRONMENT = "VICTORXIAO"
    }

    stages {
        stage('Build') {
            steps {
                echo "fetch the source code from the directory path specified by the environment variable ,$DIRECTORY_PATH"
                echo "Compiling the code and generating any necessary artifacts"
            }
        }
        stage('Test') {
            steps {
                echo "Completed unit tests"
                echo "Completed integration tests"
            }
        }
        stage('Code Quality Check') {
            steps {
                echo "Check the quality of the code."
            }
        }
        stage('Deploy') {
            steps {
                echo "deploy the application to a testing enviroment,$TESTING_ENVIRONMENT specified by the environment variable."
            }
        }
        stage('Approval') {
            steps {
                echo "Waiting for manual approval.."
                sleep(time: 1, unit: 'SECONDS')
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deployed the code to the production environment, $PRODUCTION_ENVIRONMENT"
            }
        }
        
    }
}
