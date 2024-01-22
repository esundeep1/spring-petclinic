pipeline {
    agent any
    tools {
        maven 'maven3.9'
    }
    stages {
        stage('Checkout') {
            steps {
                // Cloning the repository
                git branch: 'main', url: 'https://github.com/esundeep1/spring-petclinic.git'
            }
        }
        stage('Build and Test') {
            steps {
                // Building the project and running unit tests with Maven
                sh 'mvn clean package'
                // If you have specific goals for integration tests, add them here
                // sh 'mvn verify'
            }
        }
    } 
    post {
        always {
            // Actions to perform after the pipeline execution
            echo 'Build process completed.'
        }
        success {
            // Actions to perform if the pipeline is successful
            echo 'Build successful!'
            // Archiving artifacts (e.g., JAR or WAR files)
            archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            // If test reports are generated, they can be archived or published here as well
            junit '**/target/surefire-reports/TEST-*.xml'
        }
        failure {
            // Actions to perform if the pipeline fails
            echo 'Build failed!'
        }
    }
}
