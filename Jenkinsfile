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
            emailext (
                subject: "Jenkins Build ${currentBuild.result}: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                body: """
                    <html>
                    <body>
                        <h2>Build ${currentBuild.result}</h2>
                        <p><strong>Job:</strong> ${env.JOB_NAME}</p>
                        <p><strong>Build Number:</strong> ${env.BUILD_NUMBER}</p>
                        <p><strong>Build Status:</strong> ${currentBuild.result}</p>
                        <p><strong>Build URL:</strong> <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                        <p><strong>Duration:</strong> ${currentBuild.durationString}</p>
                        <hr>
                        <h3>Console Output:</h3>
                        <pre>${currentBuild.rawBuild.getLog(50).join('\n')}</pre>
                    </body>
                    </html>
                """,
                to: 'ziadmedhat301@gmail.com',
                from: 'ziadmehat999@gmail.com',
                mimeType: 'text/html'
            )
        }
        
        success {
            echo 'Build succeeded! Email notification sent.'
        }
        
        failure {
            echo 'Build failed! Email notification sent.'
        }
    }
}