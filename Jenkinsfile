pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building project..."
            }
        }
        stage('Test') {
            steps {
                echo "Running tests..."
            }
        }
    }

    post {
        success {
            // ✅ Slack Notification
            slackSend(channel: '#johncena',
                      color: 'good',
                      message: "✅ SUCCESS: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (<${env.BUILD_URL}|Open Job>)")

            // ✅ Email Notification
            emailext (
                subject: "✅ SUCCESS: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """
                Hello Team,

                The Jenkins job *${env.JOB_NAME}* build #${env.BUILD_NUMBER} has succeeded.

                👉 Check details: ${env.BUILD_URL}

                Regards,  
                Jenkins
                """,
                to: "santosgoal2024@gmail"
            )
        }

        failure {
            // ❌ Slack Notification
            slackSend(channel: '#johncena',
                      color: 'danger',
                      message: "❌ FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (<${env.BUILD_URL}|Check Logs>)")

            // ❌ Email Notification
            emailext (
                subject: "❌ FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """
                Hello Team,

                The Jenkins job *${env.JOB_NAME}* build #${env.BUILD_NUMBER} has **FAILED**.

                👉 Check console logs here: ${env.BUILD_URL}

                Regards,  
                Jenkins
                """,
                to: "santosgoal2024@gmail"
            )
        }

        always {
            echo "Build finished with status: ${currentBuild.currentResult}"
        }
    }
}
