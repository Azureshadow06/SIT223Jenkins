pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Build the code using Maven"
                echo 'mvn clean package'
            }
            
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Run unit tests using JUnit"
                echo 'mvn test'

                echo "Run integration tests using a tool like Selenium"
                echo 'mvn integration-test'
            }
            post {
                success{
                    emailext(
                        to: "xiao2364390271@gmail.com",
                        subject: "Unit and Integration Tests - ${currentBuild.currentResult}",
                        body: "Unit and Integration Tests status: ${currentBuild.currentResult}"
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                
                echo "Integrate a code analysis tool (e.g., SonarQube)"
                echo 'mvn sonar:sonar'
                
            }
        }
        stage('Security Scan') {
            steps {
                
                echo "Perform a security scan using a tool (e.g., OWASP ZAP)"
                echo 'owasp-zap -cmd -quickurl http://localhost:8080'
                
            }
        }
        stage('Deploy to Staging') {
            steps {
                
                echo "Deploy the application to a staging server (e.g., AWS EC2 instance) using a deployment tool (e.g., Ansible)"
                echo 'ansible-playbook -i staging-inventory deploy.yml'
                
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                
                echo "Run integration tests on the staging environment"
                echo 'mvn integration-test'
                
            }
        }
        stage('Deploy to Production') {
            steps {
                
                echo "Deploy the application to a production server (e.g., AWS EC2 instance) using a deployment tool (e.g., Ansible)"
                echo 'ansible-playbook -i production-inventory deploy.yml'
                
            }
        }
    }
}
