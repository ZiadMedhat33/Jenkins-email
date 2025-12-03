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
                from: "ziadmehat999@gmail.com",
                to: "ziadmedhat301@gmail.com",
                subject: "Jenkins Build SUCCESS",
                body: "The build completed successfully."
            )
        }

        failure {
            mail(
              from: "ziadmehat999@gmail.com",
               to: "ziadmedhat301@gmail.com",
                subject: "Jenkins Build FAILED",
                body: "The build has failed. Check Jenkins for details."
            )
        }
    }
}
//..