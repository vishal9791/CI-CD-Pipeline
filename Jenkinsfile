pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/var/www/myapp"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/vishal9791/CI-CD-Pipeline.git
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                sshagent(['deploy-key']) {
                    sh '''
                    rm -rf ${DEPLOY_DIR}/*
                    cp -r * ${DEPLOY_DIR}/
                    pm2 restart all || pm2 start app.js
                    '''
                }
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
