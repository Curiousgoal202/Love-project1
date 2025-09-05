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
            slackSend(channel: '#johncena',
                      color: 'good',
                      message: "✅ SUCCESS: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (<${env.BUILD_URL}|Open Job>)")
        }
        failure {
            slackSend(channel: '#johncena',
                      color: 'danger',
                      message: "❌ FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (<${env.BUILD_URL}|Check Logs>)")
        }
    }
}
