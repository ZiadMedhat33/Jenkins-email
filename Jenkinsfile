pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
    }
    
    post {
        always {
            mail to: 'ziadmedhat301@gmail.com',
                 from: 'ziadmehat999@gmail.com',
                 subject: "Jenkins Build: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                 body: "Build Status: ${currentBuild.result}\n\nJob: ${env.JOB_NAME}\nBuild Number: ${env.BUILD_NUMBER}"
        }
    }
}//