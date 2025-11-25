pipeline {
    agent any

    // Make sure you have added a Secret Text credential in Jenkins with ID 'vercel-token'
    environment {
        VERCEL_TOKEN = credentials('vercel-token')

    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your GitHub repo
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Test') {
            steps {
                // Run tests but pass if no tests exist
                bat 'npm test -- --passWithNoTests'
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploy to Vercel') {
            steps {
                // Deploy to Vercel using the token correctly (Windows syntax)
             bat 'npx vercel --prod --token %VERCEL_TOKEN% --confirm'
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }
        success {
            echo "Build and Deployment succeeded!"
        }
        failure {
            echo "Pipeline failed. Check the logs above."
        }
    }
}
