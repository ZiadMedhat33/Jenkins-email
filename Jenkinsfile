pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building the project..."   // Replace this with your actual build commands
            }
        }
    }

    post {
        always {
            // Send an email after the build, whether it succeeds or failss
            emailext (
                subject: "Build #${env.BUILD_NUMBER} - ${currentBuild.currentResult}",
                body: """Hello,

The Jenkins build for project '${env.JOB_NAME}' has finished.

Build Number: ${env.BUILD_NUMBER}
Build Status: ${currentBuild.currentResult}

Check the build details here: ${env.BUILD_URL}
""",
                to: "ziadmedhat301@gmail.com"   // Replace with your email
            )
        }
    }
}
