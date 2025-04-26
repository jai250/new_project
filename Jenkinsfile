pipeline {
    agent any

    environment {
        APP_NAME = "my-node-app"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
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
              echo 'Deploying the application...'
                sh '''
                  mkdir -p /tmp/deploy_app
                  cp -r * /tmp/deploy_app/
                  echo "Application deployed to /tmp/deploy_app"
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Build and Deployment Successful!'
        }
        failure {
            echo '❌ Build Failed.'
        }
    }
}
