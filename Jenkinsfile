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
                echo 'Edited comment for testing...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
            post {
                success {
                    emailext (
                        to: 'jeoff.reyes.jr@gmail.com',
                        subject: "Test Stage: ${currentBuild.currentResult}",
                        body: "The test stage has completed with status: ${currentBuild.currentResult}.",
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        to: 'jeoff.reyes.jr@gmail.com',
                        subject: "Test Stage FAILED: ${currentBuild.currentResult}",
                        body: "The test stage has failed.",
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
                success {
                    emailext (
                        to: 'jeoff.reyes.jr@gmail.com',
                        subject: "Security Scan Stage: ${currentBuild.currentResult}",
                        body: "The security scan has completed with status: ${currentBuild.currentResult}.",
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        to: 'jeoff.reyes.jr@gmail.com',
                        subject: "Security Scan Stage FAILED: ${currentBuild.currentResult}",
                        body: "The security scan has failed.",
                        attachLog: true
                    )
                }
            }
        }
    }
}
