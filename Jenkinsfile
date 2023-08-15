pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Build the code using Maven"
                    sh 'mvn clean package'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo "Run unit tests using JUnit"
                    sh 'mvn test'

                    echo "Run integration tests using a tool like Selenium"
                    sh 'mvn integration-test'
                }
            }
        }
    }
}
