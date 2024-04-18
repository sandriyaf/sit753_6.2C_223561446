pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Build the code using Maven
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests using JUnit
                sh 'mvn test'
                // Run integration tests using Selenium or similar
                sh 'mvn integration-test'
            }
        }
        stage('Code Analysis') {
            steps {
                // Integrate a code analysis tool like SonarQube
                // This requires SonarQube server to be configured in Jenkins
                script {
                    // Run SonarQube analysis
                    // Example: withSonarQubeEnv('SonarQube') {
                    //     sh 'mvn sonar:sonar'
                    // }
                }
            }
        }
        stage('Security Scan') {
            steps {
                // Perform security scan using tools like OWASP ZAP or SonarQube
                // This requires configuring security tools in Jenkins
                script {
                    // Run security scan
                    // Example: sh 'mvn owasp:dependency-check'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy application to staging server
                // This requires SSH credentials or other deployment configurations
                script {
                    // Example: sh 'scp target/myapp.war user@staging:/path/to/deploy'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on staging environment
                // This may involve hitting endpoints or running scripts on the staging server
                script {
                    // Example: sh 'curl http://staging:8080/test'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                // Deploy application to production server
                // This requires similar configurations as staging deployment
                script {
                    // Example: sh 'scp target/myapp.war user@production:/path/to/deploy'
                }
            }
        }
    }

    post {
        always {
            // Clean up steps or notifications
        }
        success {
            // Send notification email on success
            emailext subject: 'Pipeline Success',
                      body: 'Pipeline completed successfully.',
                      to: 'sandriyafernandes35@gmail.com'
        }
        failure {
            // Send notification email on failure
            emailext subject: 'Pipeline Failure',
                      body: 'Pipeline failed. Please check logs.',
                      to: 'sandriyafernandes35@gmail.com'
        }
    }
}
