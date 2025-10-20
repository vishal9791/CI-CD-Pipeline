pipeline {
    agent any
    environment {
        REPO_URL = 'https://github.com/vishal9791/CI-CD-Pipeline.git'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: "${REPO_URL}", branch: 'master'
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Building the project..."'
                // Add your build commands here
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
                // Add your test commands here
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Deploying the project..."'
                // Add your deployment commands here
            }
        }
    }
    post {
        success {
            echo 'Build, Test, and Deploy succeeded!'
        }
        failure {
            echo 'Build, Test, or Deploy failed.'
        }
    }
}
