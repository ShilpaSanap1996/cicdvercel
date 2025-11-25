pipeline{
    agent any

    environment{
        VERCEL_TOKEN = credentials('vercel-token')
    }
    stages{
        stage('Install'){
            step{
                bat 'npm install'
            }
        }
        stage('Test'){
            step{
                echo 'Skip Test'
            }
        }
        stage('Build'){
            step{
                bat 'npm run build'
            }
        }
        stage('Deploy'){
            step{
                bat 'npx vercel --prod --token --yes --token=%VERCEL_TOKEN%'
            }
        }
    }
}