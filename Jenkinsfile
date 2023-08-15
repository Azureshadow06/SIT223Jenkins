pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                /*Maven is a widely used build automation and project management tool. 
                It provides a structured and standardized way to manage the build of projects. 
                Maven helps to simplify the process of building, testing and deploying software.*/
                echo "Build the code using Maven"

                /*The "mvn clean package" command is a common Maven command to clean a project, compile source code, run tests, 
                and package the compiled code into a distributable format (such as a JAR or WAR file). 
                This produces executable or deployable artifacts that can be used in your application.*/
                echo 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                /*JUnit is a popular Java testing framework. It is primarily used for writing and running unit tests, 
                which focus on testing individual units or components of code in isolation.
                Unit tests help to verify that a specific part of the code works as expected and maintains the expected behavior.
                The "mvn test" command invokes JUnit to run the unit tests and ensure that the code works correctly at the component level.*/
                echo "Run unit tests using JUnit"
                ehco 'mvn test'

                /*Selenium is an open source automated testing framework widely used for testing web applications. 
                It allows you to automate the interaction of the web browser with the user interface of the application.
                The Command "mvn integration-test". Integration testing ensures that the different components of an application work together as expected.*/
                echo "Run integration tests using Selenium"
                echo 'mvn integration-test'
            }
            post {
                always{
                    emailext(
                        to: "xiao2364390271@gmail.com",
                        subject: "Unit and Integration Tests - ${currentBuild.currentResult}",
                        body: "Unit and Integration Tests status: ${currentBuild.currentResult}",
                        attachLog: true
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                /*SonarQube is an open source platform that provides continuous code quality management. 
                It is designed to help developers and teams monitor and improve the quality of their codebase by analyzing code for potential bugs,
                vulnerabilities, code smells, and adherence to coding standards.*/
                echo "Integrate a code analysis tool SonarQube"
                
                /*Execute the command mvn sonar:sonar, which triggers a SonarQube analysis of the codebase. 
                The analysis results are then sent to the SonarQube server for processing and reporting.*/
                echo 'mvn sonar:sonar'
                
            }
        }
        stage('Security Scan') {
            steps {
                /*OWASP ZAP (Zed Attack Proxy) is an open source security tool designed to find vulnerabilities in web applications. 
                It is one of the most widely used and respected web application security scanners. 
                ZAP helps identify security gaps and weaknesses in web applications by simulating various types of attacks and providing detailed reports on potential issues.*/
                echo "Perform a security scan using OWASP ZAP"

                /*This command simulates the use of OWASP ZAP. In a practical implementation, 
                we can run the OWASP ZAP tool using the command line interface or invoked in a script.
                The tool scans the URL http://localhost:8080 for security vulnerabilities.*/
                echo 'owasp-zap -cmd -quickurl http://localhost:8080'
                
            }
            post {
                always{
                    emailext(
                        to: "xiao2364390271@gmail.com",
                        subject: "Security Scan - ${currentBuild.currentResult}",
                        body: "Security Scan status: ${currentBuild.currentResult}",
                        attachLog: true
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                /*Ansible is a suite of software tools that enables infrastructure as code. It is open source, 
                and the suite includes features such as software provisioning, configuration management and application deployment. 
                Ansible is used to automate IT operations such as deploying applications, managing configurations, scaling infrastructure, 
                and other activities involving many repetitive tasks.*/
                echo "Deploy the application to a staging server using a deployment tool Ansible"

                /*The deploy.yml Ansible playbook defines the deployment tasks that need to be executed on the staging server. 
                This playbook typically includes tasks such as copying application artifacts, configuring environment variables, 
                starting services, and performing any necessary setup.*/
                echo 'ansible-playbook staging deploy.yml'
                
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                /*In this phase, Maven will be used as the tool to manage and execute the integration tests. 
                Integration testing is important to ensure that different components of an application work together as expected in real-world scenarios. 
                This phase helps to catch issues that may arise due to interactions between various parts of the application, such as databases, APIs, or external services.*/
                echo "Run integration tests on the staging environment"
                
                /*The "mvn integration-test" command invokes the Maven build lifecycle phase responsible for running integration tests.*/
                echo 'mvn integration-test'
                
            }
        }
        stage('Deploy to Production') {
            steps {
                /*This stage is responsible for deploying the application to the production server using the Ansible deployment tool.*/
                echo "Deploy the application to a production server using a deployment tool Ansible"

                /*The ansible-playbook command is used in deploy.yml to execute the Ansible playbook ( ) on the production server.*/
                echo 'ansible-playbook production deploy.yml'
                
            }
        }
    }
}
