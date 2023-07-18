pipeline {
    agent any

    triggers {
        cron('H 0 * * *') // This schedules the job to run daily at midnight
    }

    stages {
        stage('Checkout') {
            steps {
                cleanWs() // Clean workspace before checking out the code
                git branch: 'main', credentialsId: 'deploy', url: 'https://github.com/DevBarham/Nodejs-app-periodic-deployment-jenkins-cicd'
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm i' // Use "npm ci" for a clean install of dependencies
            }
        }

        stage('Test') {
            steps {
                sh 'npm test' // Run tests
            }
            post {
                success {
                    echo 'Tests passed. Proceeding with the build...'
                }
                failure {
                    echo 'Tests failed. Aborting the build.'
                    error 'Tests failed.'
                }
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build' // Add your build commands here
            }
        }

        stage('Deploy') {
            steps {
                // Add deployment steps here
                 echo 'Deploying App...'
            }
        }
    }

    post {
        always {
            // Clean up or perform any post-build actions here
             echo 'Performing post-build actions...'
        }
        success {
            echo 'Build and deployment were successful.'
        }
        failure {
            echo 'Build or deployment failed.'
            error 'Build or deployment failed.'
        }
    }
}
