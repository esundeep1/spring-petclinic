pipeline {
    agent any
    tools {
        maven 'maven3.9'
    }
    stages {
        stage('Checkout') {
            steps {
                // Cloning the repository
                git branch: 'main', url:'https://github.com/esundeep1/spring-petclinic.git'
            }
        }
        
        stage('Build') {
            steps {
                // Building the project with Maven
                sh 'mvn clean package'
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
        }
        failure {
            // Actions to perform if the pipeline fails
            echo 'Build failed!'
        }
    }
}
