pipeline {
    agent any

    // triggers {
    //     cron('H 0 * * *') // This schedules the job to run daily at midnight
    // }

    stages {

        stage("Cleanup Workspace"){
            steps {
                cleanWs()
            }
        }
        
        stage("Checkout from SCM"){
            steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/Nahsc0/Nodejs-app-periodic-deployment-jenkins-cicd'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh "ls"
                }
                
            }
        }

        stage('Test') {
            steps {
                echo "Test App..."
            }
        }

        stage('Build') {
            steps {
                echo "Build App..."
            }
        }

        stage('Deploy') {
            steps {
                 echo 'Deploying App...'
            }
        }
    }

}
