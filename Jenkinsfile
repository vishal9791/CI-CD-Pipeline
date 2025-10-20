pipeline {
    agent any

    environment {
        // Example: define environment variables here
        APP_NAME = "django-todo-cicd"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Pulling latest code from GitHub..."
                git branch: 'main', url: 'https://github.com/vishal9791/CI-CD-Pipeline.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building application..."
                // Example: for Maven or Node.js
                sh 'mvn clean package' // or 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'mvn test' // or 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                // Example: Copy files to EC2 or run Docker
                sh '''
                scp -i /path/to/key.pem target/myapp.jar ec2-user@<EC2_IP>:/home/ec2-user/
                ssh -i /path/to/key.pem ec2-user@<EC2_IP> "java -jar /home/ec2-user/myapp.jar &"
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful!'
        }
        failure {
            echo '❌ Pipeline failed. Please check logs.'
        }
    }
}
