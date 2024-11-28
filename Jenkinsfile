pipeline {
    agent any // Use any available Jenkins agent (default configuration)
    stages {
        stage('Checkout Code') {
            steps {
                // Pull the code from your GitHub repository
                checkout scm
            }
        }
        stage('Build') {
            steps {
                // Build the application (example: Maven build)
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                // Run tests
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                // Package the application (if using Docker, replace this with a Docker command)
                echo 'Packaging the application...'
            }
        }
    }
    post {
        always {
            // Always clean up the workspace
            cleanWs()
        }
        failure {
            // Notify on failure (for now, just log the failure)
            echo 'The build failed. Please check the logs.'
        }
    }
}
