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
        echo "✅ Trying to send SUCCESS email..."
        emailext (
            subject: "Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "Hello Team,\nThe build was successful.\n\nCheck here: ${env.BUILD_URL}",
            to: "santosgoal2024@gmail.com"
        )
    }
    failure {
        echo "❌ Trying to send FAILURE email..."
        emailext (
            subject: "Build FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "Hello Team,\nThe build has failed.\n\nCheck logs: ${env.BUILD_URL}",
            to: "santosgoal2024@gmail.com"
        )
    }
}
