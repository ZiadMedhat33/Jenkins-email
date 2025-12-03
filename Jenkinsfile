pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "project building"
            }
        }
    }

     post {
        success {
            mail(
                to: "ziadmedhat301@gmail.com",
                subject: "Jenkins Build SUCCESS",
                body: "The build completed successfully."
            )
        }

        failure {
            mail(
               to: "ziadmedhat301@gmail.com",
                subject: "Jenkins Build FAILED",
                body: "The build has failed. Check Jenkins for details."
            )
        }
    }
}
