pipeline{
    agent any

    environment{
        VERCEL_TOKEN = credentials('vercel-token')
    }
    stages {
        stage('Install') {
            steps {
                bat 'npm install'
            }
        }

       stage('Test') {
             steps {
               bat 'npm test -- --passWithNoTests'
    }
}


        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }
        stage('Deploy'){
            steps{
                bat 'npx vercel --prod --token --yes --token=%VERCEL_TOKEN%'
            }
        }
    }
}