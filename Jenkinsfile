pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout source code from version control
                git 'https://github.com/jrojas77/spring-petclinic.git'
            }
        }
        stage('Build') {
            steps {
                // Build your project
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                // Run unit tests
                sh 'mvn test'
            }
        }
        stage('Code Coverage') {
            steps {
                // Run Jacoco to generate code coverage reports
                sh 'mvn jacoco:prepare-agent test jacoco:report'
            }
            post {
                always {
                    // Archive code coverage reports
                    archiveArtifacts 'target/site/jacoco/index.html'
                }
            }
        }
        stage('Deploy') {
            steps {
                // Deploy your application
                // Add deployment steps here
            }
        }
    }
    
    // Define additional pipeline configurations here
}
