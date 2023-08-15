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
        stage('Code Analysis') {
            steps {
                script {
                    echo "Integrate a code analysis tool (e.g., SonarQube)"
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo "Perform a security scan using a tool (e.g., OWASP ZAP)"
                    sh 'owasp-zap -cmd -quickurl http://localhost:8080'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo "Deploy the application to a staging server (e.g., AWS EC2 instance) using a deployment tool (e.g., Ansible)"
                    sh 'ansible-playbook -i staging-inventory deploy.yml'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Run integration tests on the staging environment"
                    sh 'mvn integration-test'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo "Deploy the application to a production server (e.g., AWS EC2 instance) using a deployment tool (e.g., Ansible)"
                    sh 'ansible-playbook -i production-inventory deploy.yml'
                }
            }
        }
    }
}
