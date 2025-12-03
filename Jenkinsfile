pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Add your build commands here
                // Example: sh 'mvn clean install'
                // Example: sh 'npm install && npm run build'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add your test commands here
                // Example: sh 'mvn test'
                // Example: sh 'npm test'
            }
        }
    }
    
    post {
        always {
            mail to: 'ziadmedhat301@gmail.com',
                 from: 'ziadmehat999@gmail.com',
                 subject: "Jenkins Build ${currentBuild.result}: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                 body: """
Build Status: ${currentBuild.result}
Job: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Build URL: ${env.BUILD_URL}
Duration: ${currentBuild.durationString}

This email was sent automatically by Jenkins.
                 """
        }
        
        success {
            echo 'Build succeeded! Email notification sent.'
        }
        
        failure {
            echo 'Build failed! Email notification sent.'
        }
    }
}