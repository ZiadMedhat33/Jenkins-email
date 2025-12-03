pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Project building..."  // You can replace this with actual build steps later
            }
        }
    }

    post {
        success {
            mail(
                to: "ziadmedhat301@gmail.com",
                from: "ziadmehat999@gmail.com",  // Must match the Gmail account in Jenkins SMTP
                subject: "Jenkins Build SUCCESS",
                body: """
Hello,

The Jenkins build for your project has completed successfully.

Build Number: ${env.BUILD_NUMBER}
Job Name: ${env.JOB_NAME}
Build URL: ${env.BUILD_URL}
"""
            )
        }

        failure {
            mail(
                to: "ziadmedhat301@gmail.com",
                from: "ziadmehat999@gmail.com",  // Must match the Gmail account in Jenkins SMTP
                subject: "Jenkins Build FAILED",
                body: """
Hello,

The Jenkins build for your project has FAILED.

Build Number: ${env.BUILD_NUMBER}
Job Name: ${env.JOB_NAME}
Build URL: ${env.BUILD_URL}
"""
            )
        }
    }
}
