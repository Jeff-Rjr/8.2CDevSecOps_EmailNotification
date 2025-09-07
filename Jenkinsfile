pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Jeff-Rjr/8.2CDevSecOps_EmailNotification.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
            post {
                always {
                    emailext (
                        subject: "Test Stage: ${currentBuild.currentResult}",
                        body: "The test stage has completed with status: ${currentBuild.currentResult}.",
                        to: 'jeoff.reyes.jr@gmail.com',
                        attachLog: true
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
            }
            post {
                always {
                    emailext (
                        subject: "Security Scan Stage: ${currentBuild.currentResult}",
                        body: "The security scan has completed with status: ${currentBuild.currentResult}.",
                        to: 'jeoff.reyes.jr@gmail.com',
                        attachLog: true
                    )
                }
            }
        }
    }
}
