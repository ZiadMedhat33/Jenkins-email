pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                // Add your checkout steps here
                // e.g., git 'https://github.com/your-repo.git'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Add your build commands here
                // e.g., sh 'mvn clean install'
                // e.g., sh 'npm install && npm run build'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add your test commands here
                // e.g., sh 'mvn test'
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
                        <p><b>Job:</b> ${env.JOB_NAME}</p>
                        <p><b>Build Number:</b> ${env.BUILD_NUMBER}</p>
                        <p><b>Build Status:</b> ${currentBuild.result}</p>
                        <p><b>Build URL:</b> <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                        <p><b>Duration:</b> ${currentBuild.durationString}</p>
                        <hr>
                        <h3>Changes:</h3>
                        <p>${currentBuild.changeSets.collect { cs -> cs.items.collect { item -> "- ${item.msg} by ${item.author}" }.join('<br>') }.join('<br>')}</p>
                    </body>
                    </html>
                """,
                to: 'ziadmedhat301@gmail.com',
                from: 'ziadmehat999@gmail.com',
                replyTo: 'ziadmehat999@gmail.com',
                mimeType: 'text/html',
                attachLog: true
            )
        }
        
        success {
            emailext (
                subject: "✅ SUCCESS: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                body: """
                    <html>
                    <body style="font-family: Arial, sans-serif;">
                        <h2 style="color: green;">Build Successful! ✅</h2>
                        <p><b>Job:</b> ${env.JOB_NAME}</p>
                        <p><b>Build Number:</b> ${env.BUILD_NUMBER}</p>
                        <p><b>Build URL:</b> <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                        <p>The build completed successfully.</p>
                    </body>
                    </html>
                """,
                to: 'ziadmedhat301@gmail.com',
                from: 'ziadmehat999@gmail.com',
                mimeType: 'text/html'
            )
        }
        
        failure {
            emailext (
                subject: "❌ FAILURE: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                body: """
                    <html>
                    <body style="font-family: Arial, sans-serif;">
                        <h2 style="color: red;">Build Failed! ❌</h2>
                        <p><b>Job:</b> ${env.JOB_NAME}</p>
                        <p><b>Build Number:</b> ${env.BUILD_NUMBER}</p>
                        <p><b>Build URL:</b> <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                        <p><b>Console Output:</b> <a href="${env.BUILD_URL}console">${env.BUILD_URL}console</a></p>
                        <p>Please check the build logs for more details.</p>
                    </body>
                    </html>
                """,
                to: 'your-email@example.com, dev-team@example.com',
                mimeType: 'text/html',
                attachLog: true
            )
        }
    }
}