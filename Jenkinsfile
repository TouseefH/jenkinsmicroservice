pipeline {
    agent any

    tools {
        maven 'Maven' // Ensure this matches the name you configured in Jenkins
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'mvn clean install'
                    } else {
                        bat 'mvn clean install'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'mvn test'
                    } else {
                        bat 'mvn test'
                    }
                }
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the application...'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
        failure {
            echo 'The build failed. Please check the logs.'
        }
    }
}
